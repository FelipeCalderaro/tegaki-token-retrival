<template>
  <q-page class="flex flex-center page-color">
    <q-card class="card">
      <q-card-section>
        Copy the Token bellow and place inside the App to sign-in
        <br>
        <div style="height:25px"></div>
        <div class="row justify-center">
          <q-btn @click="copyToken">Copy</q-btn>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';
import { useMeta, copyToClipboard, useQuasar } from 'quasar'
export default defineComponent({
  name: 'PageIndex',
  setup () {
    useMeta({ title: "Tegaki Token Retrival" })
  },
  data () {
    return {
      token: ""
    }
  },
  methods: {
    setToken () {
      // https://anilist.co/#access_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImJlNWI0Y2VkZDA5YmFiOGEzNmExNjdiNDUyODAwODUwN2ViMWRlYmVkZWJlYmE1NzUzZWQ0NDg1NTA5MDExOTU5NWY5M2Y5NzQ2N2RlNmJjIn0.eyJhdWQiOiI1NDYxIiwianRpIjoiYmU1YjRjZWRkMDliYWI4YTM2YTE2N2I0NTI4MDA4NTA3ZWIxZGViZWRlYmViYTU3NTNlZDQ0ODU1MDkwMTE5NTk1ZjkzZjk3NDY3ZGU2YmMiLCJpYXQiOjE2MjY5NDE3NDYsIm5iZiI6MTYyNjk0MTc0NiwiZXhwIjoxNjU4NDc3NzQ2LCJzdWIiOiIzNzU3NzkiLCJzY29wZXMiOltdfQ.eQnrGIYlEh6HzU6jQdVPc6ViNjb0yL0Yuan0TnylEXL93FPI9PAsuupnV5WFBnskq3X0kuS8eBuJH2AXej7-1EM_z-2IQfssxEugg5oibDY2g2KSUYaH5-gHxMH34bX36322CeGSCXuDGDtWlUlsQBuHmtiq5YHlG1GOL5C6QOr2IfwNZqcMj-Y_yAB7G2MA0Mo0QhKy8kyTldaFo2ALLQxZkeq0A6fwvPCj4K78XEuSBEwYfp26NM0SBaSopoissZDy-QRl2op0D9sNwax6c9IXGrbXhWVQ4JK5pszJASBO6ItQj_1tbcI4wSi2g6OynsOWCP73kyCahPCGDcH3AbX5z_3Se6Pd31SYuij-7kfgFwL8BriQgPeE7kykIDiMuVpExggUZB93zpI-aXpgMEiCkR_qUSsStaQDp5hpfAGzULztQlRzkmiTuLG7jZJRJcFp5vhvG0V_5jGgxasgc-nTiCWSZn-EkeruHJ4unoEjCnYme3rRmvuFnW3zT-HQ2AjdGfS-ES6x13FNNyWtxRXyxoF4u95I4Atabu14AnjcpEFOnH1cyeTmXy_QjfD6Msl-CLxoVn25F_ZN0Yw-XfEpa7fs3iqzu4EFDrEnGLt77xVsproIIy4jhbCTkj55ab366ceboyaABZ_Pi1xJa4oQ-y3INo-_0a_-UgonYP0&token_type=Bearer&expires_in=31536000
      // this.token = this.$route.query.split("&")[0].split("=")[1]
      this.token = this.$route.query.access_token;
    },
    copyToken () {
      copyToClipboard(this.token)
        .then(() => { alert("Copied") })
        .catch(() => { console.log("err"); })
    }
  },
  mounted () {
    console.log(this.$route.query.access_token);
    this.setToken();

  },
})
</script>
