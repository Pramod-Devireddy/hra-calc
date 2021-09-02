<template>
    <div>
        <v-row justify="center">
            <v-col cols="8">
                <v-row>
                    <v-col>
                        Basic Salary Per Month
                    </v-col>
                    <v-col>
                        <v-text-field
                            v-model="bs"
                            label="Basic Salary"
                            type="number"
                            filled
                            hide-details
                        />
                    </v-col>
                </v-row>

                <v-row>
                    <v-col>Dearness Allowance Per Month</v-col>
                    <v-col>
                        <v-text-field
                            v-model="da"
                            label="Dearness Allowance"
                            type="number"
                            filled
                            hide-details
                        />
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>House Rent Allowance Per Month</v-col>
                    <v-col>
                        <v-text-field
                            v-model="hra"
                            label="House Rent Allowance"
                            type="number"
                            filled
                            hide-details
                        />
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>House Rent Paid Per Month</v-col>
                    <v-col>
                        <v-text-field
                            v-model="rent"
                            label="House Rent"
                            type="number"
                            filled
                            hide-details
                        />
                    </v-col>
                </v-row>
                <v-row
                    justify="center"
                    class="my-10"
                >
                    <v-btn
                        class="pa-5"
                        color="#3cb043"
                        rounded
                        @click="calculate()"
                    >
                        Calculate HRA Exemption
                    </v-btn>
                </v-row>

                <v-divider style="border-color: #FFF !important" />

                <v-row class="mt-10">
                    <v-col>HRA Received:</v-col>
                    <v-col>{{ firstOption }}</v-col>
                </v-row>
                <v-row>
                    <v-col>Rent Paid - 10% of Salary:</v-col>
                    <v-col>{{ secondOption }}</v-col>
                </v-row>
                <v-row>
                    <v-col>50% of Basic Salary:</v-col>
                    <v-col>{{ thirdOption }}</v-col>
                </v-row>
            </v-col>
        </v-row>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                bs: 0,
                da: 0,
                hra: 0,
                rent: 0,
                firstOption: 0,
                secondOption: 0,
                thirdOption: 0,
                eligibleHRA: 0
            }
        },

        methods: {
            calculate () {
                this.firstOption = this.hra * 12
                this.secondOption = (Number(this.rent) * 12) - (Number(this.bs) + Number(this.da)) * 0.1 * 12
                this.thirdOption = 0.5 * (Number(this.bs) + Number(this.da)) * 12
            }

        }
    }
</script>

<style scoped>
</style>
