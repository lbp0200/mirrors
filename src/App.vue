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
                            <v-list two-line>
                                <template v-for="item in items">
                                    <v-subheader v-if="item.header" v-text="item.header"></v-subheader>
                                    <v-divider v-else-if="item.divider" v-bind:inset="item.inset"></v-divider>
                                    <v-list-tile avatar v-else v-bind:key="item.title" @click="">
                                        <v-list-tile-avatar>
                                            <img v-bind:src="item.avatar">
                                        </v-list-tile-avatar>
                                        <v-list-tile-content>
                                            <v-list-tile-title v-html="item.title"></v-list-tile-title>
                                            <v-list-tile-sub-title v-html="item.subtitle"></v-list-tile-sub-title>
                                        </v-list-tile-content>
                                    </v-list-tile>
                                </template>
                            </v-list>
                            <template>
                                <v-expansion-panel focusable>
                                    <v-expansion-panel-content v-for="(mirror,i) in mirrors" :key="i">
                                        <div slot="header">{{ mirror.name }}</div>
                                        <v-card>
                                            <v-card-text class="grey lighten-3">
                                                <a :href="mirror.uri" rel="nofollow">{{ mirror.name }}</a>
                                                <a v-if="mirror.help" :href="mirror.help">help</a>
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
                items: [
                    {header: 'Nginx', uri: '/nginx/', help: '', content: 'nginx'},
                    {header: 'Ubuntu', uri: '/ubuntu/', help: '', content: 'nginx'},
                ]
            }
        }
    }
</script>
