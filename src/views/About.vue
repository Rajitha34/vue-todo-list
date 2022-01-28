<template>
<v-main>
    <div class="about">
        <v-img src="../assets/img6.jpg" height="200px">
            <v-row align="end" class="lightbox white--text pa-2 fill-height">
                <v-col>
                    <v-container>
                      
                    </v-container>

                </v-col>
            </v-row>

        </v-img>

    </div>
    <div class="block">
        <v-container>
            <p>Design, develop, and test digital user interfaces and layouts for applications and websites to ensure compatibility and usability across browsers or devices. Volunteers can expect to create graphics, layouts, themes, and determine functionality for applications and websites. They may also collaborate with developers to discuss what libraries of icons and components are used in the design.</p>
        </v-container>
    </div>
    <div class="block">
        <v-container>
            <h2 class="text-left">our teams</h2>
            <v-row>
                <v-col v-for="item in items" :key="item.id" cols="4">
                    <v-card flat class="mx-auto">
                        <v-img height="400px" :src="item.src">

                        </v-img>

                        <v-card-text class="text--primary text--center">
                            <div class="title">{{item.name}}</div>
                            <p>{{item.title}}</p>
                            <p>{{item.subtitle}}</p>
                        </v-card-text>

                    </v-card>
                </v-col>
            </v-row>
        </v-container>
    </div>
</v-main>
</template>

<script>
export default {
    name: "About",
    data() {
        return {
            items: [{
                    id: 1,
                    src: require("../assets/img7.webp"),
                    name: 'Rajitha',
                    title: ' Email id: chowdaryrajitha08@gmail.com',
                    subtitle: ' Github: Rajitha34'

                },
                {
                    id: 2,
                    src: require("../assets/img8.jpg"),
                    name: 'Siva nagu',
                    title: 'Email id: sivanaguallu@gmail.com',
                    subtitle: ' Github:  Siva nagu11'
                }

            ]
        };
    }
};
</script>
