<script context="module">
    export const load = async ({fetch}) => {
        const res = await fetch('/posts.json')
        if (res.ok) {
            const { posts } = await res.json()
            return {
                props: { posts }
            }
        }
    }
</script>

<script>
    export let posts
</script>

<pre>
    {JSON.stringify(posts, null, 2)}
</pre>

