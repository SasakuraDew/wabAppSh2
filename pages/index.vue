<template>
  <div class="container">
    <h1>โพสต์จาก JSONPlaceholder API</h1>
    <ul class="post-list">
      <li v-for="post in posts" :key="post.id" class="post-item">
        <h2 class="post-title">{{ post.title }}</h2>
        <p class="post-body">{{ post.body }}</p>
      </li>
    </ul>
    <div v-if="errorMessage" class="error-message">
      <p>{{ errorMessage }}</p>
    </div>
    <div v-if="loading" class="loading-message">
      <p>กำลังโหลดโพสต์...</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: [],
      errorMessage: '',
      loading: false
    };
  },
  async created() {
    this.loading = true; // ตั้งค่าสถานะการโหลดเป็นจริง
    try {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts');
      // ตรวจสอบว่าคำขอสำเร็จหรือไม่
      if (!response.ok) {
        // หากไม่สำเร็จ ให้โยนข้อผิดพลาดพร้อมสถานะ HTTP
        throw new Error(`เกิดข้อผิดพลาด HTTP! สถานะ: ${response.status}`);
      }
      this.posts = await response.json();
    } catch (error) {
      console.error('เกิดข้อผิดพลาดในการดึงข้อมูล:', error);
      // ตั้งค่าข้อความแสดงข้อผิดพลาดที่จะแสดงแก่ผู้ใช้
      this.errorMessage = 'ไม่สามารถโหลดโพสต์ได้ กรุณาลองใหม่อีกครั้งในภายหลัง';
    } finally {
      this.loading = false; // ไม่ว่าจะสำเร็จหรือล้มเหลว ก็หยุดการโหลด
    }
  }
};
</script>

<style scoped>
/* สไตล์สำหรับส่วนประกอบนี้เท่านั้น เพื่อหลีกเลี่ยงการชนกันของสไตล์ */

/* การจัดรูปแบบทั่วไปสำหรับ body */
body {
  font-family: 'Inter', sans-serif; /* ใช้ Font Inter */
  background-color: #f0f2f5; /* สีพื้นหลังอ่อนๆ */
  color: #333; /* สีข้อความเข้มขึ้นเพื่อการอ่านง่าย */
  line-height: 1.6;
  margin: 0;
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  min-height: 100vh;
}

/* Container สำหรับส่วนประกอบทั้งหมด */
.container {
  max-width: 900px;
  width: 100%; /* ทำให้ container ตอบสนองตามขนาดหน้าจอ */
  margin: 40px auto;
  padding: 30px;
  background-color: #ffffff; /* พื้นหลังสีขาวสำหรับส่วนเนื้อหา */
  border-radius: 12px; /* มุมโค้งมนเล็กน้อย */
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1); /* เงาอ่อนๆ เพื่อให้ดูมีมิติ */
  box-sizing: border-box; /* ให้ padding และ border รวมอยู่ในความกว้าง */
}

/* หัวข้อหลัก */
h1 {
  text-align: center;
  color: #2c3e50; /* สีกรมท่า */
  margin-bottom: 35px;
  font-size: 2.8em;
  padding-bottom: 15px;
  border-bottom: 3px solid #e0e0e0; /* เส้นใต้หัวข้อ */
  position: relative;
}

h1::after {
  content: '';
  position: absolute;
  left: 50%;
  bottom: -3px;
  transform: translateX(-50%);
  width: 60px;
  height: 3px;
  background-color: #4CAF50; /* สีเขียวสดใส */
  border-radius: 2px;
}

/* สไตล์รายการโพสต์ */
.post-list {
  list-style: none; /* ลบจุดนำหน้า */
  padding: 0;
  margin: 0;
}

/* สไตล์แต่ละโพสต์ */
.post-item {
  background-color: #fdfdfd; /* พื้นหลังอ่อนมากสำหรับแต่ละโพสต์ */
  border: 1px solid #e9ecef; /* เส้นขอบบางๆ */
  border-radius: 10px;
  margin-bottom: 25px;
  padding: 25px;
  transition: transform 0.3s ease, box-shadow 0.3s ease; /* เอฟเฟกต์โฮเวอร์ที่นุ่มนวล */
  box-sizing: border-box; /* ให้ padding และ border รวมอยู่ในความกว้าง */
}

.post-item:hover {
  transform: translateY(-7px); /* ยกขึ้นเมื่อชี้เมาส์ */
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15); /* เงาที่ชัดเจนขึ้นเมื่อชี้เมาส์ */
}

/* หัวข้อโพสต์ */
.post-title {
  color: #3498db; /* สีฟ้าสดใส */
  font-size: 1.8em;
  margin-top: 0;
  margin-bottom: 10px;
  text-transform: capitalize; /* ทำให้ตัวอักษรแรกเป็นตัวพิมพ์ใหญ่ */
  line-height: 1.3;
}

/* เนื้อหาโพสต์ */
.post-body {
  color: #555;
  font-size: 1.1em;
  line-height: 1.7;
  margin-bottom: 0;
}

/* ข้อความแสดงข้อผิดพลาด */
.error-message {
  background-color: #fce4e4; /* สีแดงอ่อน */
  color: #c0392b; /* สีแดงเข้ม */
  padding: 15px;
  border-radius: 8px;
  margin-top: 20px;
  text-align: center;
  font-weight: bold;
}

/* ข้อความกำลังโหลด */
.loading-message {
  text-align: center;
  margin-top: 20px;
  color: #7f8c8d; /* สีเทา */
  font-style: italic;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .container {
    margin: 20px auto;
    padding: 20px;
  }

  h1 {
    font-size: 2em;
    margin-bottom: 25px;
  }

  .post-item {
    padding: 20px;
    margin-bottom: 20px;
  }

  .post-title {
    font-size: 1.5em;
  }

  .post-body {
    font-size: 1em;
  }
}

@media (max-width: 480px) {
  .container {
    margin: 10px;
    padding: 15px;
    border-radius: 8px;
  }

  h1 {
    font-size: 1.8em;
    margin-bottom: 20px;
  }

  h1::after {
    width: 40px;
  }

  .post-item {
    padding: 15px;
    margin-bottom: 15px;
    border-radius: 8px;
  }

  .post-title {
    font-size: 1.3em;
  }

  .post-body {
    font-size: 0.95em;
  }
}
</style>
