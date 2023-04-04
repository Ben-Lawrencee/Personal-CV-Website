<template>
    <section id="Education">
        <h1 class="text-bubble">Education</h1>
        <Timeline :entries="entries"/>
    </section>
</template>

<script>
import Timeline from '@/components/Timeline.vue';

export default {
    name: "Education",
    components: { Timeline },
    data() {
        return {
            entries: [
                {
                    startDate: new Date(2019, 0),
                    endDate: new Date(2021, 12),
                    type: "Full Time",
                    name: "Wintec City Campus",
                    brief: "Polytechnic based in Hamilton",
                    subs: [
                        {
                            title: "Level 7 Bachelor's in Software Engineering",
                        },
                        {
                            title: "Level 6 Diploma in Information Technology",
                        },
                        {
                            title: "Level 5 Certificate in Information Technology",
                        }
                    ]
                },
                {
                    startDate: new Date(2015, 0),
                    endDate: new Date(2018, 12),
                    name: "Hamilton Boys' High School",
                    subs: [
                        {
                            title: "Excellence in Year 12 IT",
                        }
                    ]
                },
            ]
        }
    }
}
</script>

<style lang="scss" scoped>

#Education > h1 {
    margin-bottom: 80px;
}

</style>