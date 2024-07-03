<script setup>

const items = JSON.parse(localStorage.getItem('items') );
</script>

<template>
  <VRow>
    <VCol cols="12">
      <VCard title="Top Scores">
        <VCardText>
          <VTable>
            <thead>
              <tr>
                <th class="text-uppercase text-left">
                  Name
                </th>
                <th>
                  Score
                </th>
                <th>
                  Date
                </th>
              </tr>
            </thead>

            <tbody>
              <tr
                v-for="item, index in items"
                :key="index"
              >
                <td class="text-left">
                  {{ item.name }}
                </td>
                <td class="text-center">
                  {{ item.score }}
                </td>
                <td class="text-center">
                  {{ item.date }}
                </td>
              </tr>
            </tbody>
          </VTable>
        </VCardText>
      </VCard>
    </VCol>
  </VRow>
</template>
