<template>
  <div>
    <nav class="flex items-center justify-between bg-blue-900 p-6">
      <div class="flex items-center flex-shrink-0 mr-6 text-white text-xl">
        Bush Labs
      </div>
    </nav>

    <div class="mt-5 mx-16 px-2">
      <div class="mb-5">
        <h2 class="text-2xl text-gray-800">About Me</h2>
        <div class="ml-3">
          <p>Hi, my name is <span class="p-name">David Bush</span>.</p>
          This is really just a place for me to experiment and explore some web
          concepts and to keep track of a few things. See the "Stuff I Like" and
          "Todo" sections below.
        </div>
      </div>

      <div class="mb-5">
        <h2 class="text-2xl text-gray-800">Currently Working On</h2>
        <ul class="ml-2">
          <li><code>[*]</code> Switching bushlabs.com to use Nuxt</li>
          <li><code>[*]</code> Switching bushlabs.com to use Tailwind CSS</li>
        </ul>
      </div>

      <div class="mb-5">
        <h2 class="text-2xl text-gray-800">Todo</h2>
        <ul class="ml-2">
          <li><code>[ ]</code> Add email to find me</li>
          <li><code>[ ]</code> Add items to "Stuff I Like" section</li>
        </ul>
      </div>

      <div class="mb-5">
        <h2 class="text-2xl text-gray-800">Stuff I Like</h2>
        <ul class="ml-3">
          <li>
            <a
              href="https://indieweb.org"
              class="text-blue-600 hover:underline hover:text-blue-900"
              >IndieWeb</a
            >
          </li>
          <li>
            <a
              href="https://github.com/philc/vimium"
              class="text-blue-600 hover:underline hover:text-blue-900"
              >Vimium</a
            >
          </li>
          <li>
            <a
              href="https://bonsaimirai.com/"
              class="text-blue-600 hover:underline hover:text-blue-900"
              >Mirai</a
            >
          </li>
        </ul>
      </div>

      <div class="mb-5">
        <h2 class="text-2xl text-gray-800">Find Me</h2>
        <div class="ml-3">
          <p>You may find me here:</p>
          <ul name="me">
            <li>
              <a
                class="text-blue-600 hover:underline hover:text-blue-900"
                href="https://github.com/davidb7"
                rel="me"
                >@davidb7</a
              >
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>
