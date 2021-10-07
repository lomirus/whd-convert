<script lang="ts">
    let input = "";
    let output = "";

    async function update() {
        try {
            const res = await fetch("http://wuhaoda.life:11451/info", {
                method: "POST",
                body: JSON.stringify({
                    data: input,
                }),
            });
            const json: Wrapper = await res.json();
            output = json.data;
        } catch (err) {
            alert(err)
        }
    }
</script>

<main>
    <div class="wrapper">
        <textarea bind:value={input} placeholder="Input Something here..." />
        <textarea bind:value={output} placeholder="Here is the output" />
    </div>
    <button on:click={update}>✈️</button>
</main>

<style>
    :root {
        margin: 40px;
        overflow: hidden;
    }

    .wrapper {
        display: grid;
        height: calc(100vh - 80px);
        column-gap: 80px;
        grid-template-columns: 1fr 1fr;
        width: 100%;
    }

    textarea {
        padding: 12px;
        outline: none;
        border-radius: 5px;
        border-color: #dcdfe6;
        resize: none;
    }

    textarea:focus {
        transition: all ease 0.1s;
        border-color: #409eff;
    }

    button {
        position: fixed;
        right: 50px;
        bottom: 50px;
        transform: translate(-50%, -50%);
        width: 80px;
        height: 80px;
        border-radius: 50%;
        border: none;
        background: #409eff;
        color: #ffffff;
        font-size: 32px;
        cursor: pointer;
        transition: all ease 0.1s;
    }

    button:hover {
        background-color: #66b1ff;
    }
    button:active {
        background-color: #0d84ff;
    }
</style>
