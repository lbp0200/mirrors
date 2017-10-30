<template>
    <v-app light>

        <v-toolbar fixed app :clipped-left="clipped">
            <v-toolbar-title v-text="title"></v-toolbar-title>
            <v-spacer></v-spacer>
        </v-toolbar>

        <main>
            <v-content>
                <v-container fluid>
                    <v-slide-y-transition mode="out-in">
                        <v-layout column align-center>
                            <blockquote>
                                &#8220;First, solve the problem. Then, write the code.&#8221;
                                <footer>
                                    <small>
                                        <em>&mdash;John Johnson</em>
                                    </small>
                                </footer>
                            </blockquote>
                            <template>
                                <v-expansion-panel focusable>
                                    <v-expansion-panel-content v-for="(mirror,i) in mirrors" :key="i">
                                        <div slot="header">{{ mirror.name }}</div>
                                        <v-card>
                                            <v-card-text class="grey lighten-3">
                                                <a :href="mirror.uri" rel="nofollow">{{ mirror.name }}</a>
                                                <a :href="mirror.help">help</a>
                                                <br>
                                                {{ mirror.content }}
                                            </v-card-text>
                                        </v-card>
                                    </v-expansion-panel-content>
                                </v-expansion-panel>
                            </template>
                        </v-layout>
                    </v-slide-y-transition>
                </v-container>
            </v-content>
        </main>
        <v-footer :fixed="fixed" app>
            <span>&copy; 2017</span>
        </v-footer>
    </v-app>
</template>

<script>
    export default {
        data() {
            return {
                clipped: false,
                drawer: true,
                fixed: false,
                miniVariant: false,
                right: true,
                rightDrawer: false,
                title: '萝卜皮开源软件镜像',
                mirrors: [
                    {name: 'nginx', uri: '/nginx/', help: '', content: 'nginx'},
                    {name: 'ubuntu', uri: '/ubuntu/', help: '', content: 'nginx'},
                ]
            }
        }
    }
</script>
