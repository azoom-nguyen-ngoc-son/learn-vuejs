<template>
    <div class="container-page">
        <div class="header">
            <h1 class="title">My Boards</h1>
            <div class="popupAddBoards text-center">
                <v-dialog v-model="dialog" width="350">
                    <template v-slot:activator="{ on, attrs }">
                        <v-btn elevation="2" small v-bind="attrs" v-on="on">
                            ADD BOARDS
                        </v-btn>
                    </template>
                    <v-card>
                        <div class="popupAddBoards-Header">
                            <v-card-title class="text-h6 lighten-2 ">
                                Add Board
                            </v-card-title>
                            <box-icon class="iconX" @click="dialog = false" name='x'></box-icon>
                        </div>
                        <div class="inputAddBoards">
                            <v-text-field  v-model="this.boardItemName" :rules="nameRules" label="Board title"
                                required></v-text-field>
                        </div>
                        <div class="chooseColorInput">
                            <v-btn @click="isColorInput = true" v-show="!isColorInput" elevation="1">CHOOSE BOARD
                                COLOR</v-btn>
                            <v-color-picker v-model="this.boardItemColorCode" v-show="isColorInput" class="ma-2"
                                hide-inputs>
                            </v-color-picker>
                        </div>
                        <v-btn :disabled="isDisable">SUBMIT</v-btn>
                        <v-divider></v-divider>
                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn color="primary" text @click="dialog = false">
                                I accept
                            </v-btn>
                        </v-card-actions>
                    </v-card>
                </v-dialog>
            </div>
        </div>
        <div class="content">
            <div class="content-boxItem">
                <h3 class="title"> box 1</h3>
                <p class="created"> {{ this.dayCreated }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ContainerPage',
    data() {
        return {
            dayCreated: '',
            dialog: false,
            boardItemName: "",
            boardItemColorCode: "",
            isColorInput: false,
            isDisable: true,
            nameRules: [
                v => !!v || 'Name is required',
                v => v.length <= 10 || 'Name must be less than 10 characters',
            ],
        }

    },
    created() {
        this.dayCreated = this.getDate()
    },

    methods: {
        takeValueInput(){
            console.log("dssds");
        },
        getDate() {
            const today = new Date();
            // const date = today.getFullYear() + '-' + (today.getMonth()+1) + '-' + today.getDate();
            return today
            // var currentDate = new Date();
            // console.log(currentDate);
            // var currentDateWithFormat = new Date().toJSON()
            // console.log(currentDateWithFormat);
            // return currentDateWithFormat
        }
    }

}
</script>

<style lang="scss" scoped>
.container-page {
    padding: 40px 150px;

    >.header {
        display: flex;
        padding-bottom: 20px;
        justify-content: space-between;
    }
}

.content-boxItem {
    display: inline-block;
    padding: 20px;
    background-color: red;
    border-radius: 4px;

    >.title {
        font-size: 20px;
        padding-bottom: 10px;
    }

    >.created {
        font-size: 8px;
    }
}

.popupAddBoards-Header {
    display: flex;
    justify-content: space-between;
    padding: 20px;

    >.iconX {
        cursor: pointer;
        margin-top: 18px;
    }
}

.inputAddBoards {
    padding: 0 30px;
}

.chooseColorInput {
    display: flex;
    width: 100%;
    justify-content: center;
    padding: 0 20px;

    >.v-btn {
        width: 100%;
    }
}
</style>