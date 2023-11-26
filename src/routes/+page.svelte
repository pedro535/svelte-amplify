<script>
    import axios from 'axios';
    import { API_URL } from "$lib/env";
    let files;

    function handleSubmit() {
        const formData = new FormData();
        formData.append('file', files[0]);

        axios.post(`${API_URL}/files/`, formData, {
            headers: {
                'Content-Type': 'multipart/form-data'
            }
        }).then(res => {
            console.log(res);
        }).catch(err => {
            console.log(err);
        });
    }

</script>


<div class="container mx-auto py-14">
    <p class="text-5xl font-bol pb-14">
        Svelte on AWS Amplify
    </p>

    <a href="/teste" class="underline text-blue-700">Teste Tab</a>

    <div class="my-10">
        <form on:submit|preventDefault={handleSubmit}>
            <input bind:files id="material" name="material" type="file" />
            <button type="submit">Submit</button>
        </form>
    </div>

</div>
