<script>
  import Logo3 from "./Logo3.svelte"
  import { Email } from "$lib/smtp"
  import { createForm } from "svelte-forms-lib"
  import * as yup from "yup"

  let thanks = false

  const { form, errors, handleSubmit, handleChange } = createForm({
    initialValues: {
      username: "",
      email: "",
      phone: "",
      message: "",
    },
    validationSchema: yup.object().shape({
      username: yup
        .string()
        .min(3, "Не меньше 3 символов")
        .max(30, "Не больше 30 символов")
        .required("Имя обязательно")
        .trim(),
      email: yup
        .string()
        .email("Введите правильный email")
        .required("Электронная почта обязательна")
        .trim(),
      message: yup
        .string()
        .min(3, "Не меньше 5 символов")
        .max(250, "Слишко большой текст. Сократите.")
        .required("Сообщение обязательно")
        .trim(),
    }),
    onSubmit: ({ username, email, phone, message }) => {
      Email.send({
        Host: "smtp.gmail.com",
        Username: "ploskergroupe@gmail.com",
        Password: "ploskergroupe4321#",
        To: "ploskergroupe@gmail.com",
        From: email,
        Subject: "www.plosker-groupe.ru",
        Body: message + " " + username + " " + phone,
      })
        .then((message) => console.log(message))
        .then(() => (thanks = true))
    },
  })
</script>

<div id="contact-info" class="pt-12 lg:pt-20 bg-slate-800">
  <div class="container-fluid max-w-screen-2xl">
    <h2
      class="text-4xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-cyan-300 to-blue-500 sm:text-5xl sm:leading-none lg:text-6xl text-center"
    >
      Контактная информация
    </h2>
  </div>
  <div class="py-16 container-fluid max-w-screen-2xl lg:grid lg:grid-cols-5">
    <div class="bg-slate-800 pb-12 lg:py-16 lg:col-span-2 xl:pr-12">
      <div class="max-w-lg mx-auto">
        <Logo3 />
        <!-- <p class="mt-3 text-lg leading-6 text-gray-500">Nullam risus blandit ac aliquam justo ipsum. Quam mauris volutpat massa dictumst amet. Sapien tortor lacus arcu.</p> -->
        <dl class="mt-8 text-base text-slate-300 space-y-5">
          <div>
            <dt class="sr-only">Адрес</dt>
            <dd class="flex">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="flex-shrink-0 h-6 w-6 pt-1 text-cyan-400"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                stroke-width="2"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"
                />
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"
                />
              </svg>
              <a
                aria-label="На карте"
                href="https://yandex.ru/maps/11463/evpatoria/house/prospekt_pobedy_37/Z0oYdQNmSUABQFpvfX14d3hiYQ==/?indoorLevel=1&ll=33.346279%2C45.196289&utm_source=main_stripe_big&z=19.31"
                class="ml-3 text-lg text-slate-100"
              >
                г.&nbsp;Евпатория, пр-т&nbsp;Победы,&nbsp;37, оф.&nbsp;2
              </a>
            </dd>
            <dt class="sr-only">Адрес</dt>
            <dd class="flex mt-4">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="flex-shrink-0 h-6 w-6 pt-1 text-cyan-400"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                stroke-width="2"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"
                />
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"
                />
              </svg>
              <a
                aria-label="На карте"
                href="https://yandex.ru/maps/29128/genichesk/house/tsentralna_vulytsia_87a/Z00YcQ9lQEQFQFpsfX13eXRjZg==/?ll=34.785912%2C46.168802&utm_source=main_stripe_big&z=16"
                class="ml-3 text-lg text-slate-100"
              >
              г.&nbsp;Геническ, ул.&nbsp;Центральная,&nbsp;87-А
              </a>
            </dd>
          </div>
          <div>
            <dt class="sr-only">Телефон</dt>
            <dd class="flex">
              <!-- Heroicon name: outline/phone -->
              <svg
                class="flex-shrink-0 h-6 w-6 pt-1 text-cyan-400"
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
              <a
                aria-label="Позвонить по телефону"
                href="tel:+79789461229"
                class="ml-3 text-lg text-slate-100 font-semibold"
              >
                <span
                  ><span class="font-normal text-slate-300">+7&nbsp;978</span
                  >&nbsp;946-12-29</span
                >
              </a>
            </dd>
          </div>
          <div>
            <dt class="sr-only">Телефон</dt>
            <dd class="flex">
              <!-- Heroicon name: outline/phone -->
              <svg
                class="flex-shrink-0 h-6 w-6 pt-1 text-cyan-400"
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
              <a
                aria-label="Позвонить по телефону"
                href="tel:+79789461228"
                class="ml-3 text-lg text-slate-100 font-semibold"
              >
                <span
                  ><span class="font-normal text-slate-300">+7&nbsp;978</span
                  >&nbsp;946-12-28</span
                >
              </a>
            </dd>
          </div>
          <div>
            <dt class="sr-only">Телефон</dt>
            <dd class="flex">
              <!-- Heroicon name: outline/phone -->
              <svg
                class="flex-shrink-0 h-6 w-6 pt-1 text-cyan-400"
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
              <a
                aria-label="Позвонить по телефону"
                href="tel:+79162105934"
                class="ml-3 text-lg text-slate-100 font-semibold"
              >
                <span
                  ><span class="font-normal text-slate-300">+7&nbsp;916</span
                  >&nbsp;210-59-34</span
                >
              </a>
            </dd>
          </div>
          <div>
            <dt class="sr-only">Email</dt>
            <dd class="flex">
              <!-- Heroicon name: outline/mail -->
              <svg
                class="flex-shrink-0 h-6 w-6 pt-1 text-cyan-400"
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
              <a
                aria-label="Email"
                href="mailto:plosker-groupe@ya.ru"
                class="ml-3 text-lg text-slate-100">plosker-groupe@ya.ru</a
              >
            </dd>
          </div>
          <div>
            <dt class="sr-only">Telegram</dt>
            <dd class="flex">
              <svg
                class="flex-shrink-0 h-6 w-6 pt-1 text-cyan-400"
                xmlns="http://www.w3.org/2000/svg"
                width="1em"
                height="1em"
                viewBox="0 0 24 24"
                ><path
                  fill="currentColor"
                  d="M21.945 2.765a1.552 1.552 0 0 0-1.572-.244L2.456 9.754a1.543 1.543 0 0 0 .078 2.884L6.4 13.98l2.095 6.926c.004.014.017.023.023.036a.486.486 0 0 0 .093.15a.49.49 0 0 0 .226.143c.01.004.017.013.027.015h.006l.003.001a.448.448 0 0 0 .233-.012c.008-.002.016-.002.025-.005a.495.495 0 0 0 .191-.122c.006-.007.016-.008.022-.014l3.013-3.326l4.397 3.405c.267.209.596.322.935.322c.734 0 1.367-.514 1.518-1.231L22.469 4.25a1.533 1.533 0 0 0-.524-1.486zM9.588 15.295l-.707 3.437l-1.475-4.878l7.315-3.81l-4.997 4.998a.498.498 0 0 0-.136.253zm8.639 4.772a.54.54 0 0 1-.347.399a.525.525 0 0 1-.514-.078l-4.763-3.689a.5.5 0 0 0-.676.06L9.83 19.07l.706-3.427l7.189-7.19a.5.5 0 0 0-.584-.797L6.778 13.054l-3.917-1.362A.526.526 0 0 1 2.5 11.2a.532.532 0 0 1 .334-.518l17.914-7.233a.536.536 0 0 1 .558.086a.523.523 0 0 1 .182.518l-3.261 16.015z"
                /></svg
              >
              <a
                aria-label="Telegram"
                href="https://t.me/ploskergroupe_nalog"
                class="ml-3 text-lg text-slate-100">t.me/ploskergroupe_nalog</a
              >
            </dd>
          </div>
          <div>
            <dt class="sr-only">Vkontakte</dt>
            <dd class="flex">
              <svg class="flex-shrink-0 h-6 w-6 pt-1 text-cyan-400" xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 1024 1024"><path fill="currentColor" d="M3 248c0-38 26-53 58-55l149 1c9 0 17 6 20 15c34 110 76 178 126 255c3 6 8 9 13 9c4 0 8-2 11-7l3-11l1-173c0-25-12-29-40-33c-11-2-18-12-18-22c0-2 0-4 1-6c14-43 58-65 120-65l56-1c46 0 88 20 88 79v227c4 3 8 5 13 5c8 0 18-5 26-18c52-73 111-160 119-206c0-2 1-3 2-5c11-22 39-37 51-41c2-1 5-2 9-2h155l10 1c15 0 26 10 31 19c9 14 7 29 8 35v7c-15 91-119 193-163 259c-6 8-9 15-9 22c0 6 3 12 8 18l146 184c8 11 12 24 12 35c0 33-31 52-61 55l-17 1H779c-3 0-5 1-8 1c-17 0-31-9-41-19c-32-39-63-79-94-118c-6-8-8-9-14-13c-7 29-13 59-20 89l-3 17c-5 18-18 37-42 42l-14 1h-98C272 830 117 584 8 277c-3-8-5-19-5-29zm601 259c-26 0-55-15-55-43V234c0-27-12-37-45-37l-57 2c-32 0-50 5-65 15c23 11 44 26 44 68v176c-3 35-32 58-60 58c-19 0-36-11-46-29c-45-68-83-132-116-224l-9-26l-133-1c-18 0-16 1-16 10c0 6 1 14 2 19l21 56c109 282 246 467 376 467h100c14 0 13-17 16-27l19-88c4-9 7-17 14-24c8-8 17-11 26-11c19 0 37 15 49 29l85 108c7 11 13 13 17 13h165c16 0 30-5 30-15c0-3-1-7-3-10L818 582c-12-15-17-30-17-45c0-16 6-32 16-46c42-63 132-153 153-227l3-13c-1-5-1-9-2-14H814c-10 4-18 10-24 18l-6 19c-23 64-86 152-131 213c-15 14-32 20-49 20z"/></svg>
              <a
                aria-label="Vkontakte"
                href="https://vk.com/ploskergroupe"
                class="ml-3 text-lg text-slate-100">vk.com/ploskergroupe</a
              >
            </dd>
          </div>
        </dl>
        <div class="mt-10 flex">
          <a
            aria-label="Позвонить по WhatsApp"
            class="group w-full sm:w-auto flex items-center justify-center px-7 py-5 border border-slate-700 bg-slate-900 hover:bg-slate-700 rounded-lg shadow-lg transition duration-200"
            href="https://api.whatsapp.com/send?phone=+79162105934"
          >
            <svg
              class="h-8 w-8 mr-3"
              width="600"
              height="603"
              viewBox="0 0 600 603"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <g clip-path="url(#clip0_163_109)">
                <path
                  d="M512.566 87.6283C456.162 31.1533 381.162 0.0344567 301.255 0C136.594 0 2.59331 134.036 2.52739 298.784C2.50821 351.447 16.2603 402.853 42.3993 448.167L0.0194092 603L158.378 561.452C202.009 585.261 251.135 597.806 301.127 597.827H301.254H301.255C465.89 597.827 599.911 463.767 599.981 299.026C600.008 219.181 568.962 144.107 512.566 87.6283V87.6283ZM301.255 547.361H301.158C256.598 547.337 212.901 535.367 174.786 512.737L165.715 507.357L71.7419 532.01L96.8316 440.367L90.9217 430.972C66.0657 391.427 52.9438 345.728 52.9625 298.804C53.0171 161.87 164.394 50.4677 301.349 50.4677C367.67 50.4953 430.005 76.3614 476.885 123.302C523.763 170.242 549.561 232.642 549.541 299.005C549.483 435.944 438.103 547.361 301.255 547.361V547.361Z"
                  fill="#94A3B8"
                />
                <path
                  d="M13.7327 585.82L54.1767 438.06C29.2253 394.816 16.1039 345.754 16.1196 295.507C16.1851 138.287 144.066 10.3774 301.192 10.3774C377.453 10.4119 449.028 40.1077 502.843 94.0043C556.669 147.901 586.294 219.54 586.263 295.73C586.198 452.953 458.309 580.874 301.203 580.874C301.192 580.874 301.211 580.874 301.203 580.874H301.076C253.368 580.859 206.49 568.876 164.855 546.171L13.7327 585.82V585.82Z"
                  fill="url(#paint0_linear_163_109)"
                />
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M227.437 171.936C221.91 159.641 216.091 159.395 210.833 159.18C206.532 158.995 201.609 159.007 196.693 159.007C191.774 159.007 183.78 160.857 177.019 168.244C170.255 175.632 151.192 193.49 151.192 229.812C151.192 266.138 177.634 301.237 181.32 306.167C185.009 311.089 232.364 388.009 307.36 417.601C369.688 442.194 382.372 437.302 395.9 436.072C409.429 434.841 439.553 418.217 445.703 400.976C451.852 383.74 451.852 368.966 450.007 365.877C448.163 362.801 443.243 360.955 435.864 357.263C428.484 353.571 392.211 335.709 385.446 333.247C378.682 330.786 373.762 329.556 368.843 336.947C363.923 344.331 349.791 360.955 345.486 365.877C341.182 370.811 336.877 371.426 329.498 367.735C322.119 364.031 298.355 356.244 270.164 331.093C248.229 311.527 233.421 287.361 229.116 279.97C224.811 272.586 228.655 268.587 232.356 264.906C235.669 261.599 239.735 256.288 243.425 251.977C247.107 247.666 248.337 244.59 250.797 239.667C253.256 234.737 252.026 230.427 250.182 226.735C248.337 223.043 233.997 186.534 227.437 171.936V171.936Z"
                  fill="#E2E8F0"
                />
                <path
                  d="M510.126 86.6788C454.37 30.8521 380.231 0.0911013 301.241 0.0561523C138.47 0.0561523 6.00752 132.553 5.94209 295.411C5.9229 347.469 19.5171 398.285 45.356 443.079L3.46313 596.134L160.004 555.062C203.135 578.597 251.696 591 301.115 591.019H301.24H301.241C463.986 591.019 596.468 458.499 596.537 295.649C596.564 216.722 565.874 142.509 510.126 86.6788V86.6788ZM301.241 541.134H301.146C257.096 541.111 213.9 529.278 176.224 506.908L167.257 501.589L74.3621 525.959L99.1635 435.368L93.3215 426.081C68.7509 386.99 55.7795 341.816 55.7987 295.43C55.8523 160.069 165.95 49.9455 301.334 49.9455C366.895 49.9726 428.512 75.5419 474.855 121.943C521.195 168.345 546.696 230.028 546.677 295.631C546.619 430.996 436.517 541.134 301.241 541.134Z"
                  fill="#E2E8F0"
                />
              </g>
              <defs>
                <linearGradient
                  id="paint0_linear_163_109"
                  x1="299.998"
                  y1="585.82"
                  x2="299.998"
                  y2="10.3784"
                  gradientUnits="userSpaceOnUse"
                >
                  <stop stop-color="#1E293B" />
                  <stop offset="1" stop-color="#64748B" />
                </linearGradient>
                <clipPath id="clip0_163_109">
                  <rect width="600" height="603" fill="white" />
                </clipPath>
              </defs>
            </svg>
            <p
              class="text-slate-300 group-hover:text-white transition duration-200"
            >
              Связаться по&nbsp;<span class="font-bold">WhatsApp</span>
            </p></a
          >
        </div>
      </div>
    </div>
    <div
      id="contacts"
      class="pb-12 px-6 sm:px-12 bg-slate-900 lg:col-span-3 border border-slate-700 rounded-lg shadow-lg"
    >
      {#if thanks}
        <div
          class="text-slate-100 text-2xl text-center h-full p-6 grid place-content-center"
        >
          <p
            class="text-slate-100 text-2xl lg:text-4xl font-semibold font-bitter"
          >
            Спасибо!
          </p>
          <p
            class="mt-3 text-slate-100 text-base sm:text-lg lg:text-xl font-normal"
          >
            Сообщения и заявки рассматриваются в рабочие часы
          </p>
          <p class="mt-3 text-slate-300 text-lg lg:text-xl font-normal">
            ПН-ПТ 9:00-18:00
          </p>
        </div>
      {:else}
        <div class="max-w-lg mx-auto lg:max-w-none">
          <h3
            class="py-16 text-2xl lg:text-3xl text-slate-100 font-bitter font-bold"
          >
            Оставьте сообщение или&nbsp;заявку
          </h3>
          <form
            on:submit|preventDefault={handleSubmit}
            class="grid grid-cols-1 gap-y-6"
          >
            <div>
              <label for="username" class="sr-only">Имя</label>
              <input
                type="text"
                name="username"
                id="username"
                autocomplete="username"
                class="block w-full shadow-sm py-3 px-4 bg-slate-800 text-slate-100 placeholder-slate-300 focus:ring-slate-600 focus:border-slate-600 border-slate-700 rounded-md"
                placeholder="Имя"
                on:change={handleChange}
                bind:value={$form.username}
              />
              {#if $errors.username}
                <small
                  class="block my-1 text-xs lg:text-base italic text-slate-400"
                  >{$errors.username}</small
                >
              {/if}
            </div>
            <div>
              <label for="email" class="sr-only">Электронная почта</label>
              <input
                id="email"
                name="email"
                type="email"
                autocomplete="email"
                class="block w-full shadow-sm py-3 px-4 bg-slate-800 text-slate-100 placeholder-slate-300 focus:ring-slate-600 focus:border-slate-600 border-slate-700 rounded-md"
                placeholder="Электронная почта"
                on:change={handleChange}
                bind:value={$form.email}
              />
              {#if $errors.email}
                <small
                  class="block my-1 text-xs lg:text-base italic text-slate-400"
                  >{$errors.email}</small
                >
              {/if}
            </div>
            <div>
              <label for="phone" class="sr-only">Телефон</label>
              <input
                type="text"
                name="phone"
                id="phone"
                autocomplete="tel"
                class="block w-full shadow-sm py-3 px-4 bg-slate-800 text-slate-100 placeholder-slate-300 focus:ring-slate-600 focus:border-slate-600 border-slate-700 rounded-md"
                placeholder="Телефон (необязательно)"
                on:change={handleChange}
                bind:value={$form.phone}
              />
              {#if $errors.phone}
                <small
                  class="block my-1 text-xs lg:text-base italic text-slate-400"
                  >{$errors.phone}</small
                >
              {/if}
            </div>
            <div>
              <label for="message" class="sr-only">Сообщение</label>
              <textarea
                id="message"
                name="message"
                rows="4"
                class="block w-full shadow-sm py-3 px-4 bg-slate-800 text-slate-100 placeholder-slate-300 focus:ring-slate-600 focus:border-slate-600 border-slate-700 rounded-md"
                placeholder="Сообщение"
                on:change={handleChange}
                bind:value={$form.message}
              />
              {#if $errors.message}
                <small
                  class="block my-1 text-xs lg:text-base italic text-slate-400"
                  >{$errors.message}</small
                >
              {/if}
            </div>
            <div>
              <button
                aria-label="Отправить"
                type="submit"
                class="w-full lg:w-auto inline-flex justify-center py-3 px-6 border border-transparent shadow-sm text-base font-medium rounded-md text-slate-800 hover:text-slate-900 bg-slate-100 hover:bg-slate-300 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-slate-500 transition duration-200"
                >Отправить</button
              >
            </div>
          </form>
        </div>
      {/if}
    </div>
  </div>
</div>
