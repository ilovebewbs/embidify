<script>
    let webhook = "" || localStorage.getItem('webhook');
    let avatar;
    let username;
    let author;
    let title;
    let description;
    let footer;
    let image_link;
    const sendEmbed = async()=>{
        try {
            localStorage.setItem('webhook', webhook);
            const config = {
                method: 'post',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    username:username,
                    avatar_url:avatar,
                    embeds:[{
                        author:{
                            name:author
                        },
                        title:title,
                        description:description,
                        image:{
                            url:image_link
                        },
                        footer:{
                            text:footer
                        }
                    }]
                })
            }
            await fetch(webhook,config);
        } catch (error) {
    
            console.log(error);
        }
    }
</script>
<main>
    <div class="justify-center grid grid-cols-2 gap-5 p-8 bg-gray-200 border border-blue-800 rounded-2xl">
        <div>
            <label for="" class=" font-bold">
                Webhook URL
            </label>
            <input bind:value={webhook} type="text" class=" border border-black rounded-3xl">
        </div>
        <div>
            <label for="" class=" font-bold">
                Username
            </label>
            <input  bind:value={username} type="text" class=" border border-black rounded-3xl" id="username">
        </div>
        <div>
            <label for="" class=" font-bold">
                Avatar URL
            </label>
            <input  bind:value={avatar} type="text" class="border border-black rounded-3xl" id="avatar">
        </div>
        <div>
            <label for="" class=" font-bold">Embed title</label>
            <input  bind:value={title} type="text" class="border border-black rounded-3xl" id="title">
        </div>
        <div>
            <label for="" class=" font-bold">Description</label>
            <input  bind:value={description} type="text" class="border border-black rounded-3xl" id="description">
        </div>
        <div>
            <label for="" class=" font-bold">Embed Author</label>
            <input  bind:value={author} type="text" class="border border-black rounded-3xl">
        </div>
        <div>
            <label for="" class=" font-bold">Footer</label>
            <input  bind:value={footer} type="text" class="border border-black rounded-3xl">
        </div>
        <div>
            <label for="" class=" font-bold">Image link inside the embed</label>
            <input  bind:value={image_link} type="text" class="border border-black rounded-3xl">
        </div>
    </div>
    <div class=" flex justify-center mt-5">
        <button  on:click={sendEmbed} class=" bg-blue-600 hover:bg-blue
         text-white rounded-full font-bold px-11 py-3">
            SEND
        </button>
    </div>
</main>

<style></style>