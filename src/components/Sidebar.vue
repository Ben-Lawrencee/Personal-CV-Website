<template>
    <aside v-show="true">
        <div class="top-bar">
            <nav>
                <button>
                    <img src="@/assets/up-arrow-1.svg"/>
                </button>
                <button>
                    <img src="@/assets/contact.svg"/>
                </button>
                <button>
                    <img src="@/assets/work.svg"/>
                </button>
                <button>
                    <img src="@/assets/education.svg"/>
                </button>
                <!-- Potentially adding Projects -->
                <!-- <button> 
                    <img src="@/assets/projects.svg"/>
                </button> -->
            </nav>
        </div>

        <div class="spacer"/>

        <div class="contacts bottom-bar">
            <button>
                <img src="@/assets/Phone.svg"/>
            </button>
            <button>
                <img src="@/assets/Email.svg"/>
            </button>
            <button class="highlighted">
                Download CV
                <img src="@/assets/Download.svg"/>
            </button>
        </div>
    </aside>
</template>

<script>
export default {
    name: "Sidebar"
}
</script>

<style lang="scss" scoped>
@import '@/GlobalVariables.scss';

aside {
    position: fixed;
    top: 0;
    right: 0;

    height: 100%;

    display: flex;
    flex-direction: column;
    justify-content: space-between;

    --right-padding: 10px;
    padding-inline: var(--right-padding);

    --svg-size: min(1.8rem, 40px);
    --blade-inset: calc(var(--svg-size) / 2 + 7px);

    .title {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: flex-end;

        font-size: 1.8rem;
        color: white;
        font-weight: 700;

        margin-bottom: 10px;
    }
}

.menu-toggle {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}


.top-bar {
    position: relative;

    padding-top: 10px;

    &::before {
        content: '';

        position: absolute;

        right: var(--blade-inset);
    
        width: 2px;
        height: 100%;
        background-color: $primary;
    }
}

.bottom-bar {
    position: relative;

    padding-bottom: 10px;

    &::before {
        content: '';

        position: absolute;

        right: var(--blade-inset);
    
        width: 2px;
        height: 100%;
        background-color: $primary;
    }
}

button {
    position: relative;

    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 10px;

    width: min-content;

    text-align: right;
    padding: 6px;
    cursor: pointer;
    
    border: 2px solid $primary;
    border-radius: 100%;

    background-color: $dark;
}

button img {
    height: var(--svg-size);
    width: var(--svg-size);
}

button.highlighted {
    width: max-content;
    padding-inline: 20px;
    
    font-weight: 700;
    
    border-radius: 2em;
    background-color: $primary;
}

nav {
    display: flex;
    flex-direction: column;
    
    align-items: flex-end;

    gap: 10px;  
}

.contacts {
    display: flex;
    flex-direction: column;
    align-items: flex-end;

    gap: 20px;
}

.spacer {
    align-self: flex-end;
    flex-grow: 1;
    width: 2px;
    margin-right: var(--blade-inset);
    background: 
        linear-gradient(to bottom, 
            $primary, 
            transparent, 
            transparent, 
            $primary);
}

@media (max-height: 700px) {
    .spacer {
        background: $primary;
    }
}

</style>