<script context="module">
    export const load = async ({ fetch }) => {
        const res = await fetch('/posts.json')
        if (res.ok) {
            const { posts } = await res.json()
            posts.reverse()
            return {
                props: { posts }
            }
        }
    }
</script>

<script>
    export let posts
</script>

<svelte:head>
    <title>ploxxy's blog</title>
</svelte:head>

<h1 class="text-4xl mt-8 mb-10 font-extrabold text-center">
    Welcome to ploxxy's blog
</h1>

<div class="grid gap-4 md:grid-cols-2 grid-cols-1">
    {#each posts as { title, slug, excerpt, coverImage, tags }}
        <div class="card bg-primary-content text-center shadow-md rounded-xl">
            <figure>
                <img class="rounded-sm" src={coverImage.url} alt={`Cover image for ${title}`}>
            </figure>
            <div class="card-body">
                <h2 class="title">{title}</h2>
                <p>{excerpt}</p>
                <div class="flex justify-center mt-5 space-x-2">
                    {#each tags as tag}
                        <span class="badge badge-primary rounded-xl">{tag}</span>
                    {/each}
                </div>
                <div class="justify-center card-actions">
                    <a href={`/posts/${slug}`} class="rounded-2xl btn btn-outline btn-primary">Read &rArr;</a>
                </div>
            </div>
        </div>
    {/each}
</div>
