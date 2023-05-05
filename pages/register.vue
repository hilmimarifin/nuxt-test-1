<template>
    <div>
        <div class="card card-side bg-base-100 shadow-xl">
            <figure><img src="https://plus.unsplash.com/premium_photo-1665657351427-efdfbf01fb81?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=880&q=80" alt="Movie" /></figure>
            <div class="card-body max-w-sm ">
                <form class="space-y-6" @submit.prevent="saveData">
                    <div>
                        <div class="form-control w-full max-w-xs ">
                            <label class="label">
                                <span class="label-text">Name</span>
                            </label>
                            <input type="text" v-model="name" placeholder="Type here"
                                class="input input-bordered input-primary w-full max-w-xs" />
                        </div>
                    </div>
                    <div>
                        <div class="form-control w-full max-w-xs">
                            <label class="label">
                                <span class="label-text">Email</span>
                            </label>
                            <input type="email" v-model="email" placeholder="Type here"
                                class="input input-bordered input-primary w-full max-w-xs" />
                        </div>
                    </div>
                    <div class="form-control w-full max-w-xs">
                        <label class="label">
                            <span class="label-text">Country</span>
                        </label>
                        <select v-model="country" class="select select-bordered select-primary">
                            <option disabled selected>Pick one</option>
                            <option v-for="cty in countryList" :key="cty.countryCode" :value="cty.countryCode">{{
                                cty.countryName }}
                            </option>

                        </select>
                    </div>
                    <div class="form-control w-full max-w-xs">
                        <label class="label">
                            <span class="label-text">City</span>
                        </label>
                        <select v-model="city" class="select select-bordered select-primary">
                            <option disabled selected>Pick one</option>
                            <option v-for="city in cityFiltered" :key="city.cityCode" :value="city.cityCode">{{
                                city.cityName }}
                            </option>
                        </select>
                    </div>

                    <div class="modal-action">
                        <button type="submit" class="btn">
                            Save
                        </button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script setup>

const countryList = [
    {
        "countryName": "Malaysia",
        "countryCode": "MYS"
    },
    {
        "countryName": "Singapore",
        "countryCode": "SIN"
    },
    {
        "countryName": "Indonesia",
        "countryCode": "IDN"
    },
    {
        "countryName": "India",
        "countryCode": "NDI"
    }
]

const cityList = [
    {
        "cityName": "Kuala Lumpur",
        "cityCode": "KLU",
        "countryCode": "MYS"
    },
    {
        "cityName": "Jaipur",
        "cityCode": "JIP",
        "countryCode": "NDI"
    },
    {
        "cityName": "Jakarta",
        "cityCode": "JKT",
        "countryCode": "IDN"
    },
    {
        "cityName": "Penang",
        "cityCode": "PEN",
        "countryCode": "MYS"
    },
    {
        "cityName": "Bandung",
        "cityCode": "BDO",
        "countryCode": "IDN"
    }
]

const name = ref("")
const email = ref("")
const country = ref([])
const city = ref([])
const cityFiltered = ref([])

const getCityList = (countryCode) => cityList?.filter(city => city.countryCode === countryCode)

watch(country, (data, prev) => cityFiltered.value = getCityList(data))

const saveData = () => {
    console.log("name: ", name.value);
    console.log("email: ", email.value);
    console.log("country: ", country.value);
    console.log("city: ", city.value)
}
</script>

<style lang="scss" scoped></style>