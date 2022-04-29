<div class="navbar mb-2 shadow-lg bg-neutral text-neutral-content">
    <div class="px-2 mx-2 navbar-start">
        <span class="text-lg font-bold">
            Blog
        </span>
    </div>

    <div class="navbar-end">
        <button class="btn btn-square" on:click={function() { document.getElementById("html").setAttribute("data-theme", document.getElementById("html").getAttribute("data-theme") == "light" ? "halloween" : "light")}}>
            🌗
        </button>
    </div>
</div>