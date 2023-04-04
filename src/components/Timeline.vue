<template>
    <TransitionGroup name="entry" tag="ol" class="timeline">
        <li class="entry" v-for="(entry, index) in entries" :key="entry">

            <div :class="['content', entry.expanded ? '' : 'closed']">

                <span class="title">
                    <h1>
                        {{ entry.name }}
                    </h1>

                    <Dot v-if="entry.type"/>

                    <h2 v-if="entry.type">
                        {{ entry.type }}
                    </h2>
                </span>

                <div class="attributes">

                    <div class="dates">
                        <span> {{ getStartDate(entry.startDate) }} </span>

                        <Dot/> 
                        
                        <span :class="entry.endDate == null ? 'bolden' : ''">
                            {{ getEndDate(entry.endDate) }}
                        </span>
                    </div>

                    <span>
                        {{ getMonthsElapsed(entry.startDate, entry.endDate) }} months
                    </span>
                </div>

                <span class="description">
                    {{ entry.brief }}
                </span>

                <div class="subs">
                    <dl class="sub-entry" v-for="sub in entry.subs">
                        <dt>{{ sub.title }}</dt>
                        <dd>{{ sub.description }}</dd>
                    </dl>
                </div>

            </div>
        </li>
    </TransitionGroup>
</template>

<script>
import Dot from '@/components/Dot.vue'

export default {
    name: "Timeline",
    components: { Dot },
    methods: {
        getMonthString(monthIndex) {
            switch (monthIndex) {
                case 0:  return "Jan";
                case 1:  return "Feb";
                case 2:  return "Mar";
                case 3:  return "Apr";
                case 4:  return "May";
                case 5:  return "Jun";
                case 6:  return "Jul";
                case 7:  return "Aug";
                case 8:  return "Sep";
                case 9:  return "Oct";
                case 10: return "Nov";
                case 11: return "Dec";
            }
        },
        getStartDate(date) {
            return this.getMonthString(date.getMonth()) + " " + date.getFullYear();
        },
        getEndDate(date) {
            if (date == null)
                return "Present";

            return this.getMonthString(date.getMonth()) + " " + date.getFullYear();
        },
        getMonthsElapsed(firstDate, secondDate) {
            if (secondDate == null)
                secondDate = new Date();
                
            return ((secondDate.getFullYear() - firstDate.getFullYear()) * 12) + (secondDate.getMonth() - firstDate.getMonth()) + 1
        }
    },
    props: {
        entries: {
            required: true,
        }
    },
    data() {
        return {
            compact: false,
        }
    },
    mounted() {
        for (let entry of this.entries)
            entry.expanded = true;
    }
}
</script>

<style lang="scss">

@import '@/GlobalVariables.scss';

.timeline {
    margin: 0;
    padding: 0;

    --side-spike-offset: -20px;

    .entry {
        display: flex;
        flex-direction: row;
        
        gap: 20px;

        align-items: center;

        margin-bottom: 70px;
    }

    /*.graphic {
        align-self: flex-start;
        position: relative;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

        width: 40px;
        height: 40px;
        aspect-ratio: 1 / 1;
        
        user-select: none;
        border-radius: 50%;
        border: 2px solid $primary;

        cursor: pointer;

        &::after {
            content: '';
            
            position: absolute;
            left: 100%;
            top: calc(50% - 1px);

            height: 2px;
            width: 30px;
            
            background: linear-gradient(to right, $primary, transparent);
        }

        img {
            width: 34px;
            height: 34px;

            transition: rotate 200ms;
            border-radius: inherit;
            background-color: $primary;
        }

        &.closed img {
            rotate: -180deg;
        }
    }*/

    .attributes {
        position: relative;
        display: flex;
        flex-direction: row;
        gap: 20px;

        width: max(450px, 50%);

        margin-block: 20px;
        margin-right: 20px;

        color: white;

        &::before {
            content: '';
            position: absolute;
            left: -20px;
            top: calc(50% - 2px);

            width: 120%;
            height: 2px;
            background: linear-gradient(to right, $primary, $secondary, transparent);

            z-index: -1;
        }

        & > * {
            width: fit-content;
            min-width: max-content;
            
            display: flex;
            flex-direction: row;
    
            justify-content: center;
            align-items: center;
            gap: 10px;

            padding-inline: 10px;
            padding-block: 2px;

            border: 2px solid $secondary;
            border-radius: 2rem;
            background-color: $dark;
        }

        &:first-child {
            background: linear-gradient(to right, $primary, $secondary);
        }
    }


    .content {
        position: relative;

        padding-bottom: 50px;
        padding-right: 20px;
        width: 100%;

        .title {
            display: flex;
            flex-direction: row;
            
            align-items: center;
            justify-content: space-between;

            width: max-content;

            gap: 15px;
            
            * {
                margin: 0;
            }
        }
    }

    .subs {
        padding-left: max(20px, 5%);

        overflow: hidden;
        transition-timing-function: ease-in-out;

        .sub-entry {
            margin-top: 50px;
        }

        dt {
            margin-top: 0;
            margin-bottom: 10px;
            color: $bright-text;

            white-space: normal;
            font-size: 1.1rem;
            font-weight: 700;

            &::before {
                content: '';

                position: absolute;

                --size: 10px;
                left: calc(var(--side-spike-offset) - (var(--size) / 2) + 1px);
                translate: 0 100%;

                width: var(--size);
                height: var(--size);
                
                border-radius: 50%;
                background-color: $primary;
            }
        }

        dd {
            display: inline;
            white-space: normal;
            margin: 0;
        }

        h2, span, .sub-entry {
            display: block;
            width: 100%;
            height: 100%;
            white-space: nowrap;
            overflow: hidden;
            transition-timing-function: ease-in-out;
        }
    }




    //Animations

    .content:not(.closed) .subs {
        transition: height 300ms;
        
        .sub-entry {
            margin-top: 50px;
            transition: max-height 300ms, margin-top 300ms;
        }

        h2, span {
            transition: width 400ms 400ms, height 400ms 500ms, line-height 400ms 500ms;
        }

    }

    .content.closed .subs {
        height: 0;
        padding-top: 0;
        --shrink-time: 500ms;
        --delay: 600ms;
        transition: height var(--shrink-time) var(--delay), padding-top var(--shrink-time) var(--delay);

        .sub-entry { 
            max-height: 0;
            margin-top: 0;
            transition: max-height var(--shrink-time) var(--delay), margin-top var(--shrink-time) var(--delay);
        }

        h2, span {
            width: 0;
            height: 0;
            margin: 0;
            transition: width 400ms, margin var(--shrink-time) var(--delay), height var(--shrink-time) var(--delay), line-height var(--shrink-time) var(--delay);            transition-timing-function: ease-in-out;
        }
    }




    //Graphics

    .content::before { //Tree trunk
        content: '';
        position: absolute;

        left: var(--side-spike-offset);
        top: 0;
        height: 100%;
        width: 2px;
        background: linear-gradient(to bottom, $primary calc(100% - 100px), transparent);

        transition: height 300ms ease-in-out;
    }

}

</style>