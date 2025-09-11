<template>
    <v-col cols="12" md="10" class="mx-auto">
        <v-row>
            <v-col cols="12" lg="5" class="py-0">
                <div class="gen-info">
                    <div class="d-flex flex-column align-start ga-8">
                        <div class="text-h3 font-weight-bold d-flex flex-column ga-2">
                            <v-divider length="35" thickness="5" class="border-opacity-100 mb-2 d-none d-sm-block"/>
                            <span>Hi, I'm Kin, a</span>
                            <span class="text-accent">Full Stack</span>
                            <span class="text-accent"> Web Developer</span>
                        </div>

                        <div class="text-body-1 font-weight-light introduction pe-lg-10 d-flex flex-column ga-3">
                            <span>
                                I'm a full-stack web developer based in the Philippines, with professional experience in building dynamic and responsive web applications.
                            </span>

                            <span>
                                Proficient in both front-end and back-end technologies, I deliver seamless digital experiences by combining clean, efficient code with intuitive design.
                            </span>
                        </div>

                        <div class="d-flex flex-column ga-6">
                            <div class="d-flex align-center ga-6">
                                <v-img src="@/assets/avatar.png" width="120"/>
                                
                                <div class="d-flex flex-column ga-3">
                                    <div>
                                        <span class="text-h6 font-weight-reguar">Jestoni Kin A. Tubiano</span>
                                        <div>{{ `${countYears()} Years of Experience` }} </div>
                                    </div>

                                    <div class="d-flex flex-column ga-2">
                                        <div v-for="(contact, icontact) in contacts" :key="icontact" class="d-flex align-center ga-2 text-body-2 text-grey-lighten-1">
                                            <v-icon :icon="contact.icon" size="small"/>
                                            <span>{{ contact.text }}</span>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <a href="/CV_Tubiano.pdf" download>
                            <v-btn variant="outlined" prepend-icon="mdi-download" color="accent" height="40" rounded="xl">
                                Download CV
                            </v-btn>
                        </a>
                    </div>
                </div>
            </v-col>

            <v-col cols="12" lg="7" class="fade-on-scroll ">
                <section>
                    <p class="text-h6 text-sm-h5 font-weight-medium mb-2">Skills</p>

                    <v-row>
                        <v-col v-for="skill in skills" :key="skill.text" cols="4" sm="3">
                            <v-card height="140" variant="tonal" color="grey-darken-1" class="d-flex flex-column justify-center">
                                <div class="d-flex justify-center px-7 pb-4">                                    
                                    <v-img :src="require(`@/assets/${skill.icon}`)" height="60" max-width="60"/>
                                </div>

                                <span class="text-body-2 text-grey-lighten-1 text-center">{{ skill.text }}</span>
                            </v-card>
                        </v-col>
                    </v-row>
                </section>

                <section>
                    <p class="text-h6 text-sm-h5 font-weight-medium mb-2">Projects</p>

                    <v-row>
                        <v-col v-for="(project, iproject) in projects" :key="iproject" cols="12">
                            <v-card color="secondary" class="pa-3 pa-lg-4 d-flex flex-column ga-5">
                                <div>
                                    <div class="d-flex flex-column align-start">
                                        <p class="text-subtitle-1">{{ project.title }}</p>
                                        <p class="text-body-2 text-grey-lighten-2">{{ project.subtitle }}</p>
                                        <a :href="project.link" target="_blank" class="text-blue-lighten-2 font-weight-light text-decoration-none">
                                            {{ project.link }}
                                        </a>
                                    </div>
                                    
                                    <v-divider class="border-opacity-25 my-3"></v-divider>

                                    <div class="d-flex flex-column flex-wrap ga-3 text-body-2 font-weight-light">
                                        <div v-for="feature in project.features" :key="feature" class="d-flex align-center ga-2">
                                            <v-icon icon="mdi-circle-medium" size="x-small"/>
                                            <span>{{ feature }}</span>
                                        </div>
                                    </div>
                                </div>

                                <div>
                                    <p class="text-body-2 mb-3">Built with:</p>

                                    <div class="d-flex flex-wrap ga-3">
                                        <v-chip v-for="tech in project.builtWith" :key="tech" color="amber-lighten-1">
                                            {{ tech }}
                                        </v-chip>
                                    </div>
                                </div>
                            </v-card>
                        </v-col>
                    </v-row>
                </section>

                <section>
                    <p class="text-h6 text-sm-h5 font-weight-medium mb-2">Experience</p>

                    <v-row>
                        <v-col v-for="(v, k) in experiences" :key="k" cols="12" md="10">
                            <v-card color="secondary">
                                <div class="px-3 py-4 d-flex ga-3 align-center">
                                    <v-img :src="require(`@/assets/${v.logo}`)" height="50" min-width="60" max-width="60"/>

                                    <div>
                                        <div class="mb-3">
                                            <p class="text-body-1 font-weight-medium">{{ v.position }}</p>
                                            <span class="text-body-2 text-grey-lighten-1">{{ v.company }}</span>
                                        </div>

                                        <span class="text-body-2">{{ v.period }}</span>
                                    </div>
                                </div>
                            </v-card>
                        </v-col>
                    </v-row>
                </section>
            </v-col>
        </v-row>
    </v-col>
</template>
  
<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
name: 'Portfolio',

setup () {
    const contacts = ref<any[]>(
        [
            { icon: 'mdi-email-outline', text: 'j.kintubiano@gmail.com' },
            { icon: 'mdi-phone-outline', text: '+63 975 868 0889' }
        ]
    )

    const skills = ref<any[]>(
        [
            { text: 'React', icon: 'react.svg' },
            { text: 'Angular', icon: 'angular.svg' },
            { text: 'Vue.js', icon: 'vue.svg' },
            { text: 'Golang', icon: 'go.svg' },
            { text: '.NET Core', icon: 'dotnet.svg' },
            { text: 'Material UI', icon: 'mui.svg' },
            { text: 'Vuetify', icon: 'vuetify.svg' },
            { text: 'Angular Material', icon: 'material.svg' },
            { text: 'Bootstrap', icon: 'bootstrap.svg' },
            { text: 'Firebase', icon: 'firebase.svg' },
            { text: 'MySQL', icon: 'mysql.svg' },
            { text: 'PostgreSQL', icon: 'postgre.svg' },
        ]
    );

    const projects = ref<any[]>(
        [
            {
                title: 'SMART FARM',
                subtitle: '',
                link: 'https://smartfarm.asscat.edu.ph/',
                features: [
                    'Firebase Authentication',
                    'Real-time sensor monitoring',
                    'Live-updating graph visualizations',
                ],
                builtWith: ['React', 'Material UI', 'Node.js', 'Firebase    '],
                thumbnail: ''
            },
            {
                title: 'DTCMS',
                subtitle: 'Digital Transformation Center Monitoring System',
                link: 'https://dtcms.asscat.edu.ph/',
                features: [
                    'OAuth 2.0 Authentication',
                    'Manage IT support requests, logs security incidents, and maintain an ICT infrastructure inventory',
                    'Google Drive API',
                    'SMS Notification'
                ],
                builtWith: ['Angular', 'Angular Material', 'Bootstrap', '.NET Core', 'MySQL'],
                thumbnail: 'dtcms.png'
            },
            {
                title: 'IPMMS',
                subtitle: 'Integrated Planning Management and Monitoring System',
                link: 'https://ipmms.asscat.edu.ph/',
                features: [
                    'OAuth 2.0 Authentication',
                    'Strategic planning, budgeting, and performance monitoring',
                    'Generate Reports (Excel Format)'
                ],
                builtWith: ['Vue.js', 'Vuetify', 'Golang (Fiber)', 'MySQL'],
                thumbnail: 'ipmms.png'
            },  
        ]
    );

    const experiences = ref<any[]>(
        [
            {
                position: 'Full Stack Web Developer',
                company: 'Agusan del Sur State College of Agriculture and Technology',
                logo: 'asscat.png',
                period: 'July 2022 - Present',
            },
        ]
    )

    const countYears = () => {
        const date = new Date();
        const sYear = 2022;
        const smonth = 7 - 1;
        
        let count = date.getFullYear() - sYear;
        
        if (date.getMonth() < smonth) {
            count--;
        }
        
        return count;
    }

    return {
       contacts, skills, projects, experiences, countYears
    }
}})
</script>

<style scoped>
    .gen-info {
        display: flex;
        align-items: center;
        position: sticky;
        top: 0;
        padding: 40px 0px;
        /* font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif */
    }
    
    .introduction {
        line-height: 25px;
    }

    section {
        padding: 30px 0px 20px;
    }

    /* 1279px and up */
    @media (min-width: 1279px) {
        .gen-info {
            min-height: 100vh;
        }
    }

    /* 1279px and down */
    @media (max-width: 1279px) {   
        .gen-info {
            padding: 40px 0px 3px;
        }    

        section {
            padding: 20px 0px;
        }
    }
</style>
