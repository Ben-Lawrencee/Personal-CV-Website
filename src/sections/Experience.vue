<template>
    <section id="Experience">
        <h1 class="text-bubble">Work Experience</h1>
        <Timeline :entries="entries"/>
    </section>
</template>

<script>
import Timeline from '@/components/Timeline.vue';

export default {
    name: "Experience",
    components: { Timeline },
    data() {
        return {
            entries: [ //Months start at index 0.
                {
                    startDate: new Date(2022, 2), // "Mar 2022"
                    endDate: null,
                    type: "Full Time",
                    name: "Skyzer Technologies",
                    brief: "EFTPOS Equipment Supplier",
                    subs: [
                        {
                            title: "Junior Software Developer",
                            description: "Managing database systems, software releases, and other internal services"
                        }
                    ]
                },
                {
                    startDate: new Date(2019, 8), // "Sep 2019"
                    endDate: null,
                    type: "Volunteer",
                    name: "Lan4Life",
                    brief: "24-hour charity gaming event, 1-3 times annually, weekends only",
                    subs: [
                        {
                            title: "Discord Administrator",
                            description: "Administrator for the official Lan4Life Discord Server."
                        },
                        {
                            title: "Event Organiser and Manager",
                            description: "Organise events and host tournaments."
                        },
                        {
                            title: "Developer",
                            description: "Contributed to the development of some tournaments."
                        },
                        {
                            title: "Event Supervisor",
                            description: "Provide supervision during the event."
                        }
                    ]
                },
                {
                    startDate: new Date(2021, 11), //"Dec 2019"
                    endDate: new Date(2022, 2), //"Mar 2022"
                    type: "Part Time",
                    name: "Hayes Common",
                    brief: "4.5 Star Restaurant",
                    location: "Hayes+Common/@-37.799014,175.289468,15z/data=!4m5!3m4!1s0x0:0xd3dd7e4afe8db2cc!8m2!3d-37.799014!4d175.289468",
                    subs: [
                        {
                            title: "Kitchen Hand",
                            description: "Worked around the kitchen assiting chefs and doing dishes."
                        }
                    ]

                },
                {
                    startDate: new Date(2021, 4), //"May 2021"
                    endDate: new Date(2022, 2), //"Mar 2022"
                    type: "Casual",
                    name: "RGIS - Stocktaking Services",
                    brief: "Inventory specialists for; The Warehouse, Briscoes, Warehouse Stationary, ...",
                    subs: [
                        {
                            title: "Stocktaker",
                            description: "Efficient stocktaker for inventory management."
                        }
                    ]
                },
                {
                    startDate: new Date(2021, 6), //"Jul 2021"
                    endDate: new Date(2021, 10), //"Nov 2021"
                    type: "Part Time",
                    name: "The GIG",
                    brief: "Simulated internship by Wintec for students to gain work experience.",
                    subs: [
                        {
                            title: "Lead Developer",
                            description: "Working with a team to create a website using VueJS and GitHub, for an industry real client."
                        }
                    ]
                }
            ]
        }
    }
}
</script>

<style lang="scss" scoped>

#Experience > h1 {
    margin-bottom: 80px;
}

</style>