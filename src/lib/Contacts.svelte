<script>
  import Logo from "./Logo.svelte";
</script>

<div class="py-12 lg:py-16 bg-slate-800">
  <div class="pb-12 lg:pb-16 container-fluid max-w-screen-2xl">
    <h2
      class="text-4xl font-bold text-slate-50 sm:text-5xl sm:leading-none lg:text-6xl text-center"
    >
      Контактная информация
    </h2>
  </div>
  <div class="container-fluid max-w-screen-2xl lg:grid lg:grid-cols-5">
    <div class="bg-slate-800 pb-16 lg:col-span-2 xl:pr-12">
      <div class="max-w-lg mx-auto">
        <Logo />
        <!-- <p class="mt-3 text-lg leading-6 text-gray-500">Nullam risus blandit ac aliquam justo ipsum. Quam mauris volutpat massa dictumst amet. Sapien tortor lacus arcu.</p> -->
        <dl class="mt-8 text-base text-gray-500">
          <div>
            <dt class="sr-only">Адрес</dt>
            <dd class="flex">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="flex-shrink-0 h-6 w-6 text-gray-400"
                viewBox="0 0 20 20"
                fill="currentColor"
              >
                <path
                  fill-rule="evenodd"
                  d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z"
                  clip-rule="evenodd"
                />
              </svg>
              <p class="ml-3 text-gray-300">
                г.&nbsp;Евпатория, пр-т&nbsp;Победы,&nbsp;36, оф.&nbsp;2
              </p>
            </dd>
          </div>
          <div class="mt-6">
            <dt class="sr-only">Телефон</dt>
            <dd class="flex">
              <!-- Heroicon name: outline/phone -->
              <svg
                class="flex-shrink-0 h-6 w-6 text-gray-400"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
                />
              </svg>
              <p class="ml-3 text-gray-300">+7&nbsp;978&nbsp;138-11-59</p>
            </dd>
          </div>
          <div class="mt-3">
            <dt class="sr-only">Email</dt>
            <dd class="flex">
              <!-- Heroicon name: outline/mail -->
              <svg
                class="flex-shrink-0 h-6 w-6 text-gray-400"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
                />
              </svg>
              <p class="ml-3 text-gray-300"> plosker-groupe@ya.ru </p>
            </dd>
          </div>
        </dl>
      </div>
    </div>
    <div
      class="pb-12 px-6 sm:px-12 bg-slate-900 lg:col-span-3 rounded-lg"
    >
      <div class="max-w-lg mx-auto lg:max-w-none">
        <h4 class="py-12 text-2xl lg:text-3xl text-slate-200 font-bitter font-bold">Оставьте сообщение/заявку</h4>
        <form action="" method="POST" class="grid grid-cols-1 gap-y-6">
          <div>
            <label for="full-name" class="sr-only">Full name</label>
            <input
              type="text"
              name="full-name"
              id="full-name"
              autocomplete="name"
              class="block w-full shadow-sm py-3 px-4 bg-slate-800 placeholder-slate-400 focus:ring-slate-600 focus:border-slate-600 border-slate-700 rounded-md"
              placeholder="Имя"
            />
          </div>
          <div>
            <label for="email" class="sr-only">Электронная почта</label>
            <input
              id="email"
              name="email"
              type="email"
              autocomplete="email"
              class="block w-full shadow-sm py-3 px-4 bg-slate-800 placeholder-slate-400 focus:ring-slate-600 focus:border-slate-600 border-slate-700 rounded-md"
              placeholder="Email"
            />
          </div>
          <div>
            <label for="phone" class="sr-only">Телефон</label>
            <input
              type="text"
              name="phone"
              id="phone"
              autocomplete="tel"
              class="block w-full shadow-sm py-3 px-4 bg-slate-800 placeholder-slate-400 focus:ring-slate-600 focus:border-slate-600 border-slate-700 rounded-md"
              placeholder="Телефон"
            />
          </div>
          <div>
            <label for="message" class="sr-only">Сообщение</label>
            <textarea
              id="message"
              name="message"
              rows="4"
              class="block w-full shadow-sm py-3 px-4 bg-slate-800 placeholder-slate-400 focus:ring-slate-600 focus:border-slate-600 border-slate-700 rounded-md"
              placeholder="Сообщение"
            />
          </div>
          <div>
            <button
              type="submit"
              class="inline-flex justify-center py-3 px-6 border border-transparent shadow-sm text-base font-medium rounded-md text-slate-700 bg-slate-100 hover:bg-slate-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-slate-500"
              >Отправить</button
            >
          </div>
        </form>
      </div>
    </div>
  </div>
</div>
