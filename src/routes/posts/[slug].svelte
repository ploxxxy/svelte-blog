<script context="module">
    export const load = async ({ fetch, params }) => {
        const { slug } = params
        const res = await fetch(`/posts/${slug}.json`)
        if (res.ok) {
            const { post } = await res.json()
            return {
                props: { post }
            }
        }
    }
</script>

<script>
    export let post

    const { title, date, tags, author: {name, authorTitle, picture}, content: { html } } = post
</script>

<button class="btn mt-5" on:click={function() { history.go(-1) }}>
    &lArr; Go back
</button>

<div class="bg-primary-content p-8 my-8 rounded-xl">
    <div class="mb-5 py-6">
        <img class="rounded-md" src={post.coverImage.url} alt={`Cover image for ${title}`} />
    </div>
    
    <h1 class="text-4xl font-semibold mb-1">{title}</h1>
    
    {#if tags}
        <div class="mb-6 flex justify-between">
            <div>
                {#each tags as tag}
                    <span class="mr-1 badge badge-primary rounded-xl">
                        {tag}
                    </span>
                {/each}
            </div>
        </div>
    {/if}
    
    <a href="/" class="inline-flex items-center mb-1">
        <img src={picture.url} alt={name} class="w-12 h-12 rounded-full flex-shrink-0 object-cover object-center">
        <span class="flex-grow flex flex-col pl-4">
            <span class="title-font font-medium">{name}</span>
            <span class="text-secondary text-xs tracking-widest mt-0.5">{authorTitle}</span>
        </span>
    </a>
    
    <p class="text-secondary text-xs tracking-widest font-semibold mb-6">
        {new Date(date).toLocaleDateString('en-UK', { year: 'numeric', month: 'long', day: 'numeric' })}
    </p>
    
    <article div class="prose max-w-full">
        {@html html}
    </article>
</div>