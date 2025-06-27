<template>
  <v-app>
    <v-main class="d-flex align-center justify-center min-h-screen">
      <v-container fluid class="pa-4">
        <v-row justify="center">
          <v-col cols="12" sm="10" md="8" lg="6">
            <v-card
              class="mx-auto pa-8 text-center rounded-xl elevation-12"
              max-width="600"
              color="#F8F8F8"
            >
              <v-img
                src="https://placehold.co/150x150/4CAF50/FFFFFF?text=V"
                alt="Vuetify.js Logo"
                contain
                height="150"
                width="150"
                class="mb-6 mx-auto rounded-full border-2 border-green-500 shadow-md"
              ></v-img>

              <blockquote class="blockquote mt-4 text-h5 font-weight-medium">
                &#8220;First, solve the problem. Then, write the code.&#8221;
                <footer>
                  <small>
                    <em>&mdash;John Johnson</em>
                  </small>
                </footer>
              </blockquote>

              <v-divider class="my-6"></v-divider>

              <p class="text-body-1 grey--text text--darken-1">
                "Code is like humor. When you have to explain it, it’s bad."
                <br>
                <small><em>&mdash;Cory House</em></small>
              </p>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  // ไม่จำเป็นต้องมี data() หรือ methods สำหรับคอมโพเนนต์ง่ายๆ นี้
  // แต่ถ้าคุณมีตรรกะหรือข้อมูลที่จะใช้ คุณสามารถเพิ่มได้ที่นี่
};
</script>

<style scoped>
/* สไตล์ที่นี่จะใช้สำหรับคอมโพเนนต์นี้เท่านั้น */
.min-h-screen {
  min-height: 100vh; /* ทำให้ v-main มีความสูงขั้นต่ำเต็มหน้าจอ */
  background: linear-gradient(135deg, #e0f2f7 0%, #bbdefb 100%); /* พื้นหลังไล่ระดับสี */
}

/* ปรับแต่ง blockquote ให้ดูทันสมัยขึ้น */
.blockquote {
  font-family: 'Georgia', serif;
  color: #3f51b5; /* สีน้ำเงินเข้มจาก Vuetify */
  border-left: 5px solid #4CAF50; /* เส้นสีเขียวที่ด้านซ้าย */
  padding-left: 20px;
  margin: 20px 0;
  line-height: 1.6;
  font-style: italic; /* ทำตัวเอน */
}

.blockquote footer {
  margin-top: 15px;
  font-size: 0.9em;
  color: #757575; /* สีเทาเข้ม */
}

.blockquote small em {
  font-style: normal; /* ยกเลิกตัวเอนสำหรับชื่อผู้เขียน */
  font-weight: 500;
}

/* สไตล์สำหรับรูปภาพ Vuetify */
.v-image {
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1); /* เพิ่มเงาให้รูปภาพ */
}
</style>
