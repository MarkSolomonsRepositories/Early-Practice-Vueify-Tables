<template>
    <v-app>
        <v-app-bar >
            <v-app-bar-title>My Table</v-app-bar-title>
            <v-btn icon='mdi-plus-circle-outline' v-on:click="ExtraColumnCount+=1"></v-btn>
        </v-app-bar>
        <v-main>
            <v-table>
                <thead>
                <tr>
                    <th v-if="EditorOpen==false" class="text-left" @mouseover="hoverTag=1" @mouseleave="hoverTag=0,EditingTextCheck=false">
                        <span v-if="hoverTag==1 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name1=EditedText,EditedText=null,EditingTextCheck=false" 
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name1 }}
                        </span>                        
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==1 && EditingTextCheck==false && EditorOpen==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <th v-else>
                        <span v-if="hoverTag==1 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name1=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                            prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                            v-on:keyup.enter="columns.name1=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name1 }}
                        </span>
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==1 && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <!-- ss -->
                    <th v-if="EditorOpen==false" class="text-left" @mouseover="hoverTag=2" @mouseleave="hoverTag=0,EditingTextCheck=false">
                        <span v-if="hoverTag==2 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name2=EditedText,EditedText=null,EditingTextCheck=false" 
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name2 }}
                        </span>                        
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==2 && EditingTextCheck==false && EditorOpen==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <th v-else>
                        <span v-if="hoverTag==2 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name2=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                            prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                            v-on:keyup.enter="columns.name2=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name2 }}
                        </span>
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==2 && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <!-- ss -->
                    <th v-if="EditorOpen==false && ExtraColumnCount>=1" class="text-left" @mouseover="hoverTag=3" @mouseleave="hoverTag=0,EditingTextCheck=false">
                        <span v-if="hoverTag==3 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name3=EditedText,EditedText=null,EditingTextCheck=false" 
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name3 }}
                        </span>                        
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==3 && EditingTextCheck==false && EditorOpen==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <th v-else-if="EditorOpen==true && ExtraColumnCount>=1">
                        <span v-if="hoverTag==3 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name3=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                            prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                            v-on:keyup.enter="columns.name3=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name3 }}
                        </span>
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==3 && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <!-- ss -->
                    <th v-if="EditorOpen==false && ExtraColumnCount>=2" class="text-left" @mouseover="hoverTag=4" @mouseleave="hoverTag=0,EditingTextCheck=false">
                        <span v-if="hoverTag==4 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name4=EditedText,EditedText=null,EditingTextCheck=false" 
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name4 }}
                        </span>                        
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==4 && EditingTextCheck==false && EditorOpen==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <th v-else-if="EditorOpen==true && ExtraColumnCount>=2">
                        <span v-if="hoverTag==4 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name4=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                            prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                            v-on:keyup.enter="columns.name4=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name4 }}
                        </span>
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==4 && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <!-- ss -->
                    <th v-if="EditorOpen==false && ExtraColumnCount>=3" class="text-left" @mouseover="hoverTag=5" @mouseleave="hoverTag=0,EditingTextCheck=false">
                        <span v-if="hoverTag==5 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name5=EditedText,EditedText=null,EditingTextCheck=false" 
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name5 }}
                        </span>                        
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==5 && EditingTextCheck==false && EditorOpen==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <th v-else-if="EditorOpen==true && ExtraColumnCount>=3">
                        <span v-if="hoverTag==5 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name5=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                            prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                            v-on:keyup.enter="columns.name5=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name5 }}
                        </span>
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==5 && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <!-- ss -->
                    <th v-if="EditorOpen==false && ExtraColumnCount>=4" class="text-left" @mouseover="hoverTag=6" @mouseleave="hoverTag=0,EditingTextCheck=false">
                        <span v-if="hoverTag==6 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name6=EditedText,EditedText=null,EditingTextCheck=false" 
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name6 }}
                        </span>                        
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==6 && EditingTextCheck==false && EditorOpen==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <th v-else-if="EditorOpen==true && ExtraColumnCount>=4">
                        <span v-if="hoverTag==6 && EditingTextCheck">
                            <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                            append-icon="mdi-arrow-right-circle-outline" v-on:click:append="columns.name6=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                            prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                            v-on:keyup.enter="columns.name6=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                            single-line solo></v-text-field>
                        </span>
                        <span v-else>
                            {{ columns.name6 }}
                        </span>
                        <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==6 && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                    </th>
                    <th v-if="Object.keys(this.carrots).length != 1" class="text-left">
                        Delete 
                    </th>
                </tr>
                </thead>
                <tbody>
                    <tr
                        v-for="(carrot, carrotIndex) in carrots"
                        :key="carrot.name"
                    >
                        <td v-if="EditorOpen==false" @mouseover="hoverTag=7+carrotIndex+(carrotIndex*6)" @mouseleave="hoverTag=0,EditingTextCheck=false">
                            <span v-if="hoverTag==7+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.name=EditedText,EditedText=null,EditingTextCheck=false" 
                                single-line solo></v-text-field>
                            </span>
                            <!-- <a v-else-if=""></a> -->
                            <span v-else>
                                {{ carrot.name }}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==7+carrotIndex+(carrotIndex*6) && EditingTextCheck==false && EditorOpen==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <td v-else >
                            <span v-if="hoverTag==7+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.name=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                                prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                                v-on:keyup.enter="carrot.name=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                                single-line solo></v-text-field>
                            </span>
                            <!-- <a v-else-if=""></a> -->
                            <span v-else>
                                {{ carrot.name }}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==7+carrotIndex+(carrotIndex*6) && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <!-- ss -->
                        <td v-if="EditorOpen==false" @mouseover="hoverTag=8+carrotIndex+(carrotIndex*6)" @mouseleave="hoverTag=0,EditingTextCheck=false">
                            <span v-if="hoverTag==8+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.goal=EditedText,EditedText=null,EditingTextCheck=false" 
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{ carrot.goal }}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==8+carrotIndex+(carrotIndex*6) && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <td v-else >
                            <span v-if="hoverTag==8+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.goal=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                                prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                                v-on:keyup.enter="carrot.goal=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{ carrot.goal }}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==8+carrotIndex+(carrotIndex*6) && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <!-- ss -->
                        <td v-if="ExtraColumnCount>=1 && !EditorOpen" @mouseover="hoverTag=9+carrotIndex+(carrotIndex*6)" @mouseleave="hoverTag=0,EditingTextCheck=false">
                            <span v-if="hoverTag==9+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.value1=EditedText,EditedText=null,EditingTextCheck=false" 
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{carrot.value1}}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==9+carrotIndex+(carrotIndex*6)" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <td v-else-if="ExtraColumnCount>=1 && EditorOpen">
                            <span v-if="hoverTag==9+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.value1=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                                prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                                v-on:keyup.enter="carrot.value1=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{carrot.value1}}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==9+carrotIndex+(carrotIndex*6) && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <!-- ss -->
                        <td v-if="ExtraColumnCount>=2 && !EditorOpen" @mouseover="hoverTag=10+carrotIndex+(carrotIndex*6)" @mouseleave="hoverTag=0,EditingTextCheck=false">
                            <span v-if="hoverTag==10+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.value2=EditedText,EditedText=null,EditingTextCheck=false" 
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{carrot.value2}}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==10+carrotIndex+(carrotIndex*6)" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <td v-else-if="ExtraColumnCount>=2 && EditorOpen">
                            <span v-if="hoverTag==10+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.value2=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                                prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                                v-on:keyup.enter="carrot.value2=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{carrot.value2}}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==10+carrotIndex+(carrotIndex*6) && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <!-- ss -->
                        <td v-if="ExtraColumnCount>=3 && !EditorOpen" @mouseover="hoverTag=11+carrotIndex+(carrotIndex*6)" @mouseleave="hoverTag=0,EditingTextCheck=false">
                            <span v-if="hoverTag==11+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.value3=EditedText,EditedText=null,EditingTextCheck=false" 
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{carrot.value3}}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==11+carrotIndex+(carrotIndex*6)" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <td v-else-if="ExtraColumnCount>=3 && EditorOpen">
                            <span v-if="hoverTag==11+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.value3=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                                prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                                v-on:keyup.enter="carrot.value3=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{carrot.value3}}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==11+carrotIndex+(carrotIndex*6) && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <!-- ss -->
                        <td v-if="ExtraColumnCount>=4 && !EditorOpen" @mouseover="hoverTag=12+carrotIndex+(carrotIndex*6)" @mouseleave="hoverTag=0,EditingTextCheck=false">
                            <span v-if="hoverTag==12+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.value4=EditedText,EditedText=null,EditingTextCheck=false" 
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{carrot.value4}}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==12+carrotIndex+(carrotIndex*6)" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <td v-else-if="ExtraColumnCount>=4 && EditorOpen">
                            <span v-if="hoverTag==12+carrotIndex+(carrotIndex*6) && EditingTextCheck">
                                <v-text-field hide-details v-model="EditedText" dense flat  label="Solo" placeholder="Placeholder"
                                append-icon="mdi-arrow-right-circle-outline" v-on:click:append="carrot.value4=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false" 
                                prepend-icon="mdi-close-circle-outline" v-on:click:prepend="EditedText='',EditingTextCheck=false,EditorOpen=false"
                                v-on:keyup.enter="carrot.value4=EditedText,EditedText=null,EditingTextCheck=false,EditorOpen=false"
                                single-line solo></v-text-field>
                            </span>
                            <span v-else>
                                {{carrot.value4}}
                            </span>
                            <v-btn size="x-small" icon='mdi-pencil'  v-if="hoverTag==12+carrotIndex+(carrotIndex*6) && EditingTextCheck==false" v-on:click="EditingTextCheck=true,EditorOpen=true"></v-btn>
                        </td>
                        <!-- ss -->
                        <td v-if="Object.keys(this.carrots).length != 1">
                            <v-btn size="x-small" icon='mdi-trash-can-outline' v-on:click="CarrotValueStorage=carrotIndex,SliceObject()" ></v-btn>
                        </td>
                    </tr>
                </tbody>
            </v-table>
        </v-main>
    </v-app>
</template>

<script>
    // import { mdiPlusCircleOutline } from '@mdi/js';
    // import { aliases, mdi } from 'vuetify/lib/iconsets/mdi'
  export default {
    data () {
      return {
        EditedText: '',
        EditorOpen: false,
        EditingTextCheck: false,
        hoverTag: 0,
        CarrotValueStorage: 0,
        ExtraColumnCount: 0,
        columns: {
            name1: 'CarrotName',
            name2: 'CarrotGoal',
            name3: 'Add Title',
            name4: 'Add Title',
            name5: 'Add Title',
            name6: 'Add Title',

        },
        carrots: [
            {
                name: 'Bob',
                goal: 'Cooking',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
            {
                name: 'Linda',
                goal: 'Jumping',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
            {
                name: 'Eclair',
                goal: 'Eating',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
            {
                name: 'Cupcake',
                goal: 'Floating',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
            {
                name: 'Gingerbread',
                goal: 'Watching a movie',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
            {
                name: 'Jelly bean',
                goal: 'Standing',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
            {
                name: 'Lollipop',
                goal: 'Seeing',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
            {
                name: 'Martha',
                goal: 'Licking',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
            {
                name: 'Haroldston',
                goal: 'Going to school',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
            {
                name: 'KitKatter',
                goal: 'Living',
                value1: 'Enter Value',
                value2: 'Enter Value',
                value3: 'Enter Value',
                value4: 'Enter Value'
            },
        ],
        }
    },
    watch: {
    // whenever question changes, this function will run
        ExtraColumnCount (newExtraColumnCount){
            if (newExtraColumnCount >= 5) {
                alert("Maximum columns reached");
            }
        }
    },
    methods: {
        SliceObject: function(){
            // this.carrots.slice(this.CarrotValueStorage,this.CarrotValueStorage+1)
            // this.carrots[this.CarrotValueStorage] = null;
            for(let i=this.CarrotValueStorage;i<Object.keys(this.carrots).length;i++){
                this.carrots[i]=this.carrots[i+1]
            }
            this.carrots.pop()
        },
        RenewText: function(){
            
        }
    }
}
</script>