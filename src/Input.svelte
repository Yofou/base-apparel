<script>
    import IsEmail from 'email-format-check'

    let input = '';
    let isFalseEmail = false

    const onSubmit = () => {
        if (input.length == 0) {
            isFalseEmail = false
            return
        }

        isFalseEmail = !IsEmail(input)
    }

    const onEnter = (event) => {
        if (event.key != 'Enter') return
        onSubmit()
    }
</script>

<div class:bad={isFalseEmail}>
    <input 
        bind:value={input}
        on:keydown={onEnter}
        type="text" 
        placeholder="Email Address"
    >
    <button on:click={onSubmit}>
        <img src="./images/icon-arrow.svg" alt="arrow">
    </button>

    <img src="./images/icon-error.svg" alt="error">
</div>

{#if isFalseEmail}
    <p>Please provide a valid email</p>
{/if}

<style>
    div {
        position: relative;
        width: 435px;
        height: 55px;
        border-radius: 30px;
        border: 1px solid hsl(348, 16%, 82%);

        display: grid;
        grid-area: contact;
        grid-template: 1fr / 1fr 100px;
    }

    input {
        width: 100%;
        height: 100%;
        border: none;
        outline: none;
        font-family: var(--family);
        font-weight: 500;
        color: var(--red-600);
        border-radius: 30px;
        background: inherit;
        
        margin: 0;
        padding: 0 0 0 30px;
    }

    input::placeholder { 
        color: var(--red-300); 
        font-weight: 400;
        font-family: var(--family);
    }

    button {
        width: 100%;
        height: 110%;
        transform: translate(10%, -5%);
        border-radius: 30px;
        background: var(--grad-red);
        cursor: pointer;
        transition: background 0.1s ease-in-out, box-shadow 0.1s ease-in-out;
        box-shadow: 0 2px 15px var(--red-300);
    }

    button:focus {
        border: none;
        outline: none;
    }

    button:hover {
        background: var(--grad-red);
        box-shadow: 0 8px 25px var(--red-300);
    }

    .bad {
        border: 2px solid var(--red-500);
    }

    p {
        margin-top: 10px;
        margin-left: 30px;
        font-size: 0.8rem;
        color: var(--red-500);
        font-family: var(--family);
    }

    div > img {
        opacity: 0;
        position: absolute;
        top: 50%;
        right: calc(30% - 10px);
        transform: translate(50%, -50%);
        transition: opacity 0.1s ease-in-out;
    }

    .bad > img { opacity: 1; }

    @media (max-width: 675px) {
        div {
            place-self: center;
            width: 80%;
            height: 45px;
        }

        input, input::placeholder {
            font-size: 0.9rem;
        }

        button {
            width: 70%;
            transform: translate(50%, -5%);
            box-shadow: 0 2px 5px var(--red-300);
        }

        button:focus, button:hover { box-shadow: 0 2px 10px var(--red-300); }

        div > img {
            right: calc(30%);
        }

        p {
            font-size: 0.8rem;
            margin-left: 60px;
        }
    }
</style>