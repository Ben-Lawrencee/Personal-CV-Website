<template>
    <div class="timeline">

        <ol>

            <li class="entry" v-for="entry in entries">

                <span class="title">
                    <h1>
                        {{ entry.name }}
                    </h1>
                    <h2>
                        {{ entry.type  }}
                    </h2>
                </span>

                <span class="details">
                    {{ entry.brief }}
                    <a v-if="entry.location" :href="'https://www.google.com/maps/place/' + entry.location"><img src="@/assets/Location.svg"/>Location</a>
                </span>

                <ul>
                    <li class="sub" v-for="sub in entry.subs">
                        <h2>
                            {{ sub.title }}
                        </h2>
                        <span>
                            {{ sub.description }}
                        </span>
                    </li>
                </ul>

            </li>

        </ol>

    </div>
</template>

<script>
export default {
    name: "Timeline",
    data() {
        return {
            entries: [
                {
                    startDate: "March 2022",
                    endDate: "Current",
                    type: "Full Time",
                    name: "Skyzer Technologies",
                    brief: "EFTPOS Equipment Supplier",
                    subs: [
                        {
                            title: "Junior Software Developer",
                            description: "Managing daatabase systems, software releases, and other internal services"
                        }
                    ]
                },
                {
                    startDate: "September 2019",
                    endDate: "Current",
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
                    startDate: "December 2019",
                    endDate: "March 2022",
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
                    startDate: "May 2021",
                    endDate: "March 2021",
                    type: "Casual",
                    name: "RGIS",
                    brief: "Inventory specialists for; The Warehouse, Briscoes, Warehouse Stationary, ...",
                    subs: [
                        {
                            title: "Stocktaker",
                            description: "Efficient stocktaker for inventory management."
                        }
                    ]
                },
                {
                    startDate: "July 2021",
                    endDate: "November 2021",
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

<style lang="scss">

@import '@/GlobalVariables.scss';


.timeline {

    position: relative;

    h1::before {
        content: '';
        position: absolute;
        
        width: 20px;
        --height: 20px;
        height: var(--height);
        
        left: 0;
        // translate: 0 50%;
        translate: 0 calc(var(--height) / 2 - 3px);
        
        border: 2px solid $primary;
        border-radius: 50%;

        background-color: $dark;
    }

    padding-left: 50px;
    padding-block: 50px;

    ol {
        display: flex;
        flex-direction: column;
        margin: 0;
        padding: 0;
    }

    li {
        list-style-type: none;
        margin-bottom: 50px;
    }

    ul {
        margin-top: 20px;
    }

    .entry {

        --indent: 2ch;

        .title {
            display: flex;
            flex-direction: row;
            align-items: center;

            --gap: 10px;
            gap: var(--gap);

            color: white;

            h1::after {
                content: "·";
                color: $primary;
                margin-left: var(--gap);
            }
        }
        
        .details {
            padding-left: var(--indent);
        }

        h1, h2 {
            margin: 0;
            color: $bright-text;
        }

        .sub span {
            padding-left: var(--indent);
        }
    }

    span {
        display: flex;
        flex-direction: row;
        align-items: center;
    }
}

</style>