<script setup>
import { ref, reactive, onBeforeUpdate } from "vue";

const data = reactive({
    name: "",
    discordTag: "",
    birthday: "",
    email: "",
    text: ""
});

let buttonDisabled = ref(true);

onBeforeUpdate(() => {
    if(data.name.toString().trim().length === 0) {
        buttonDisabled.value = true;
    } else if(data.discordTag.toString().length === 0) {
        buttonDisabled.value = true;
    } else if(data.birthday.toString().trim().length === 0) {
        buttonDisabled.value = true;
    } else if(data.email.toString().trim().length === 0) {
        buttonDisabled.value = true;
    } else if(data.text.toString().trim().length === 0) {
        buttonDisabled.value = true;
    } else {
        buttonDisabled.value = false;
    }
});

const onButtonClickEvent = () => {
  alert("Dein Computer wurde gekackt!")
};

</script>

<template>
    <div class="formular">
        <h1>Du möchtest dich bewerben?</h1>
        <h2>Bitte fülle das Formular mit deinen Daten aus damit sich jemand mit dir in Verbindung setzen kann.</h2>
        <div class="row">
            <div class="item">
                <p>Dein Name:</p>
                <input class="input-small" type="text" v-model="data.name" placeholder="Marcel">
            </div>
            <div class="item">
                <p>Discord- Tag:</p>
                <input class="input-small" type="text" v-model="data.discordTag" placeholder="VIPMarcel#0001">
            </div>
        </div>
        <div class="row">
            <div class="item">
                <p>Geburtstag:</p>
                <input class="input-small" type="date" v-model="data.birthday">
            </div>
            <div class="item">
                <p>Email Adresse:</p>
                <input class="input-small" type="email" v-model="data.email" placeholder="deineemail@provider.com">
            </div>
        </div>
        <div class="row">
            <div class="item">
                <p>Deine Bewerbung:</p>
                <textarea class="input-big" style="resize: none" v-model="data.text" placeholder="Uns interessiert natürlich auch warum du genau uns gewählt hast.."/>
            </div>
        </div>
        <div class="button-section">
            <button :class="{ 'button-opend': !buttonDisabled, 'button-closed': buttonDisabled }" type="submit" :disabled="buttonDisabled" name="apply" @click="onButtonClickEvent">Bewerben</button>
        </div>
    </div>
</template>
