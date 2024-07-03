<script setup>
import { ref } from 'vue';
// import { route } from 'vue-route';

let init = {
  name: '',
  roundoff17: '',
  roundoff45: '',
  roundoff75: '',
  roundoff19: '',
  roundoff64: '',
  roundoff0: '',
  roundoff98: '',
  roundoff199: '',
  roundoff94: '',
  roundoff165: '',
  roundoff445: '',
  roundoff999: '',
};

let questions = [
   17,
   45,
   75,
   19,
   64,
   0,
   98,
   199,
   94,
   165,
   445,
   999
];

const form = ref(init);
const result = ref(null);
const valid = ref(null);

const roundTo10 = (N)=> {
  return Math.ceil(N / 10) * 10;
}
 const nameRules = [
   value => {
      if (value) return true
      return 'This is required.'
    }
  ]

const save = ()=>{ 
  if(valid.value.isValid){
    result.value = questions.filter((v,i)=>roundTo10(v)==parseInt(form.value['roundoff'+v])).length
    let items = JSON.parse(localStorage.getItem("items")) || []
    const current = new Date().toDateString()
    items.push({name:form.value.name, score:result.value, date: current})
    let results = JSON.stringify(items)
    localStorage.setItem("items", results);
  }
}
</script>

<template>
  <VRow>
    <VCol cols="12">
        <VCard title="Rounding Off nearest 10">
          <VCardText v-if="result==null" >
            
            <p class="text-primary align-center">
              <b>Select the correct answer.</b>
            </p>
          <VForm @submit.prevent="save()" ref="valid">
              <VRow>
                <!-- 👉 Name -->
                <VCol
                  cols="12"
                  md="6"
                >
                  <VTextField
                    v-model="form.name"
                    label="Full Name"
                    placeholder="John"
                    :rules="nameRules"
                  />
                </VCol>

                <VCol 
                  cols="12"
                  md="6"
                >
                  <!-- {{ form }} -->
                <!-- 👉 17 rounded off to the nearest 10 is -->
                 </VCol>
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">17 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff17"
                  >
                    <VRadio
                      label="10"
                      value="10"
                    />
                    <VRadio
                      label="20"
                      value="20"
                    />
                    <VRadio
                      label="17"
                      value="17"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 17 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">45 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff45"
                  >
                    <VRadio
                      label="50"
                      value="50"
                    />
                    <VRadio
                      label="45"
                      value="45"
                    />
                    <VRadio
                      label="40"
                      value="40"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 75 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">75 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff75"
                  >
                    <VRadio
                      label="70"
                      value="70"
                    />
                    <VRadio
                      label="80"
                      value="80"
                    />
                    <VRadio
                      label="175"
                      value="175"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 19 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">19 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff19"
                  >
                    <VRadio
                      label="20"
                      value="20"
                    />
                    <VRadio
                      label="10"
                      value="10"
                    />
                    <VRadio
                      label="19"
                      value="19"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 64 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">64 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff64"
                  >
                    <VRadio
                      label="64"
                      value="64"
                    />
                    <VRadio
                      label="70"
                      value="70"
                    />
                    <VRadio
                      label="60"
                      value="60"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 0 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">0 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff0"
                  >
                    <VRadio
                      label="10"
                      value="10"
                    />
                    <VRadio
                      label="1"
                      value="1"
                    />
                    <VRadio
                      label="0"
                      value="0"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 98 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">98 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff98"
                  >
                    <VRadio
                      label="80"
                      value="80"
                    />
                    <VRadio
                      label="100"
                      value="100"
                    />
                    <VRadio
                      label="89"
                      value="89"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 199 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">199 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff199"
                  >
                    <VRadio
                      label="190"
                      value="190"
                    />
                    <VRadio
                      label="100"
                      value="100"
                    />
                    <VRadio
                      label="200"
                      value="200"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 94 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">94 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff94"
                  >
                    <VRadio
                      label="100"
                      value="100"
                    />
                    <VRadio
                      label="94"
                      value="94"
                    />
                    <VRadio
                      label="90"
                      value="90"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 165 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">165 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff165"
                  >
                    <VRadio
                      label="160"
                      value="160"
                    />
                    <VRadio
                      label="170"
                      value="170"
                    />
                    <VRadio
                      label="150"
                      value="150"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 445 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">445 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff445"
                  >
                    <VRadio
                      label="450"
                      value="450"
                    />
                    <VRadio
                      label="440"
                      value="440"
                    />
                    <VRadio
                      label="500"
                      value="500"
                    />
                  </VRadioGroup>
                </VCol>
                <!-- 👉 999 rounded off to the nearest 10 is -->
                <VCol 
                  cols="12"
                  md="6"
                >
                  <h4 class="mb-3">999 rounded off to the nearest 10 is</h4>
                  <VRadioGroup
                    :rules="nameRules"
                    v-model="form.roundoff999"
                  >
                    <VRadio
                      label="990"
                      value="990"
                    />
                    <VRadio
                      label="1000"
                      value="1000"
                    />
                    <VRadio
                      label="909"
                      value="909"
                    />
                  </VRadioGroup>
                </VCol>
                <VCol
                  cols="12"
                  class="d-flex gap-4"
                >
                  <VBtn type="submit">
                    Submit
                  </VBtn>

                  <VBtn
                    type="reset"
                    color="secondary"
                    variant="tonal"
                  >
                    Reset
                  </VBtn>
                </VCol>
              </VRow>
            </VForm>

        </VCardText>
        <VCardText v-else>
          <p>Dear {{ form.name }},</p>
          <p>
            Your Score is <b> {{ result }} </b>  out of 12
          </p>
          <p >See Top Scores <RouterLink to="list">here</RouterLink> </p>
          
        </VCardText>
      </VCard>
    </VCol>
  </VRow>
</template>
