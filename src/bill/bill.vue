<script setup lang="ts">
    import { Bill, BillManager } from "./bill.ts";
    const bills = BillManager.getBills();
</script>

<template>
    <div style="flex-direction: row; display: flex;">
        <div class="available-bill">
            <p style="text-align: center; padding-top: 6px; margin: 0px; width: auto; height: auto">
                可用：￥{{ Math.round(BillManager.getAvailable() * 100) / 100 }}
            </p>
        </div>
        <div class="income-bill">
            <p style="text-align: center; padding-top: 6px; margin: 0px; width: auto; height: auto">
                收入：￥{{ Math.round(BillManager.getIncomes() * 100) / 100 }}
            </p>
        </div>
        <div class="outlay-bill">
            <p style="text-align: center; padding-top: 6px; margin: 0px; width: auto; height: auto">
                支出：￥{{ Math.round(BillManager.getoutlays() * 100) / 100 }}
            </p>
        </div>
    </div>
    <div class="border border-[var(--vp-c-brand-3)] rounded-[20px] p-2 m-2 flex flex-col gap-2 bg-[var(--vp-c-divider)]">
        <div class="collapse collapse-arrow rounded-[12.5px]" v-for="bill in bills">
            <input type="checkbox" />
            <div class="collapse-title font-semibold flex gap-2 bg-[var(--vp-nav-screen-bg-color)]">
                <svg
                    v-if="bill.type === 'outlay'"
                    width="28"
                    height="28"
                    style="scale: 150%; margin-top: 11px; margin-left: 6px"
                    viewBox="0 0 28 28"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg">
                    <path
                        fill="#DBBE3E"
                        d="M13.9531 25.9062C20.4922 25.9062 25.9062 20.4805 25.9062 13.9531C25.9062 7.41406 20.4805 2 13.9414 2C7.41406 2 2 7.41406 2 13.9531C2 20.4805 7.42578 25.9062 13.9531 25.9062Z" />
                    <path
                        style="fill: var(--vp-nav-screen-bg-color)"
                        d="M13.9531 19.8594C13.5078 19.8594 13.2031 19.5312 13.2031 19.0391V17.3047H10.9883C10.6484 17.3047 10.4023 17.0469 10.4023 16.707C10.4023 16.3672 10.6367 16.1094 10.9883 16.1094H13.2031V15.1836H10.9883C10.6484 15.1836 10.4023 14.9258 10.4023 14.5742C10.4023 14.2344 10.6367 13.9766 10.9883 13.9766H12.6406L9.69922 9.24219C9.59375 9.06641 9.54688 8.92578 9.54688 8.73828C9.54688 8.33984 9.875 8.02344 10.3086 8.02344C10.6133 8.02344 10.8359 8.14062 11.0117 8.42188L13.9648 13.4023L16.918 8.43359C17.082 8.16406 17.3164 8.03516 17.6094 8.03516C18.043 8.03516 18.3711 8.35156 18.3711 8.75C18.3711 8.9375 18.3359 9.07812 18.2188 9.25391L15.2891 13.9766H16.9648C17.3164 13.9766 17.5625 14.2344 17.5625 14.5742C17.5625 14.9258 17.3164 15.1836 16.9648 15.1836H14.7266V16.1094H16.9648C17.3164 16.1094 17.5625 16.3672 17.5625 16.707C17.5625 17.0469 17.3164 17.3047 16.9648 17.3047H14.7266V19.0508C14.7266 19.543 14.4102 19.8594 13.9531 19.8594Z" />
                </svg>
                <svg
                    v-if="bill.type === 'income'"
                    width="28"
                    height="28"
                    style="scale: 150%; margin-top: 11px; margin-left: 6px"
                    viewBox="0 0 28 28"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg">
                    <path
                        fill="green"
                        d="M13.9531 25.9062C20.4922 25.9062 25.9062 20.4805 25.9062 13.9531C25.9062 7.41406 20.4805 2 13.9414 2C7.41406 2 2 7.41406 2 13.9531C2 20.4805 7.42578 25.9062 13.9531 25.9062Z" />
                    <path
                        style="fill: var(--vp-nav-screen-bg-color)"
                        d="M13.9531 19.8594C13.5078 19.8594 13.2031 19.5312 13.2031 19.0391V17.3047H10.9883C10.6484 17.3047 10.4023 17.0469 10.4023 16.707C10.4023 16.3672 10.6367 16.1094 10.9883 16.1094H13.2031V15.1836H10.9883C10.6484 15.1836 10.4023 14.9258 10.4023 14.5742C10.4023 14.2344 10.6367 13.9766 10.9883 13.9766H12.6406L9.69922 9.24219C9.59375 9.06641 9.54688 8.92578 9.54688 8.73828C9.54688 8.33984 9.875 8.02344 10.3086 8.02344C10.6133 8.02344 10.8359 8.14062 11.0117 8.42188L13.9648 13.4023L16.918 8.43359C17.082 8.16406 17.3164 8.03516 17.6094 8.03516C18.043 8.03516 18.3711 8.35156 18.3711 8.75C18.3711 8.9375 18.3359 9.07812 18.2188 9.25391L15.2891 13.9766H16.9648C17.3164 13.9766 17.5625 14.2344 17.5625 14.5742C17.5625 14.9258 17.3164 15.1836 16.9648 15.1836H14.7266V16.1094H16.9648C17.3164 16.1094 17.5625 16.3672 17.5625 16.707C17.5625 17.0469 17.3164 17.3047 16.9648 17.3047H14.7266V19.0508C14.7266 19.543 14.4102 19.8594 13.9531 19.8594Z" />
                </svg>
                <div style="padding-left: 10px; padding-top: 6px; display: flex; flex-direction: column">
                    <p style="margin: 0px; font-weight: bold; line-height: 15px">{{ bill.date }}</p>
                    <p style="margin: 0px; opacity: 80%">操作员：{{ bill.operator }}</p>
                </div>
                <div class="w-fit h-auto text-right right-16 absolute flex">
                    <h3
                        v-if="bill['original-amount'] !== undefined && bill['original-unit'] !== undefined"
                        style="
                            opacity: 75%;
                            border-top: 0px;
                            margin: 0px;
                            margin-top: 8px;
                            border-right: 1px solid var(--vp-c-divider);
                            margin-right: 4px;
                            padding-right: 8px;
                            padding-top: 2px;
                        ">
                        {{ bill["original-unit"] + bill["original-amount"] }}
                    </h3>
                    <h2 style="border-top: 0px; margin: 0px; padding-top: 8px">￥{{ bill["exchanged-amount"] }}</h2>
                </div>
            </div>
            <div class="collapse-content text-sm bg-[var(--vp-nav-screen-bg-color)]">
                <div class="flex gap-2 items-center">
                    <div class="badge badge-md badge-inline text-[var(--vp-nav-screen-bg-color)]" style="--badge-color: var(--vp-c-brand-3)">
                        {{
                            bill["type"] === "income" ? "收入来源" : bill["type"] === "outlay" ? "支出目标" : "交易对象"
                        }}
                    </div>
                    {{ bill["target"] }}
                </div>
                <div class="flex gap-2 items-center mt-1">
                    <div class="badge badge-md badge-inline text-[var(--vp-nav-screen-bg-color)]" style="--badge-color: var(--vp-c-warning-1)">
                        交易内容
                    </div>
                    {{ bill["description"] }}
                </div>
            </div>
        </div>
    </div>
</template>

<style>
    div.available-bill {
        height: 40px;
        width: 150px;
        background-color: var(--vp-c-divider);
        border-radius: 10px;
        margin-left: 7.5px;
    }
    div.income-bill {
        height: 40px;
        width: 150px;
        background-color: green;
        border-radius: 10px;
        margin-left: 7.5px;
        color: white;
    }
    div.outlay-bill {
        height: 40px;
        width: 150px;
        background-color: #dbbe3e;
        border-radius: 10px;
        margin-left: 7.5px;
        color: black;
    }
</style>
