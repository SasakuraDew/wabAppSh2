<template>
  <v-app dark>
    <!-- Navigation Drawer -->
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      fixed
      app
      class="drawer-bg-custom"
    >
      <!-- User Profile Section in Drawer -->
      <v-list-item class="user-profile-section pa-4">
        <v-list-item-avatar size="64">
          <img src="https://placehold.co/64x64/FFAB00/FFFFFF?text=JD" alt="User Avatar">
        </v-list-item-avatar>
        <v-list-item-content class="ml-3">
          <v-list-item-title class="user-name text-h6 font-weight-bold">John Doe</v-list-item-title>
          <v-list-item-subtitle class="user-role grey--text text--lighten-1">Administrator</v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider class="my-3"></v-divider>

      <!-- Navigation List Items -->
      <v-list dense>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
          active-class="list-item-active-custom"
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <!-- App Bar (Header) -->
    <v-app-bar
      fixed
      app
      flat
      class="app-bar-custom elevation-4"
      color="#1F2636"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" class="white--text" />
      <v-toolbar-title class="app-bar-title white--text">{{ title }}</v-toolbar-title>
      <v-spacer />
      <!-- User profile menu in App Bar -->
      <v-menu
        offset-y
        left
        content-class="rounded-lg elevation-8"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            icon
            large
            v-bind="attrs"
            v-on="on"
            class="ml-2 user-avatar-btn"
          >
            <v-avatar size="40">
              <img src="https://placehold.co/40x40/FFAB00/FFFFFF?text=JD" alt="User Avatar">
            </v-avatar>
          </v-btn>
        </template>
        <v-list class="user-menu-list">
          <v-list-item @click="() => {}">
            <v-list-item-icon><v-icon>mdi-account</v-icon></v-list-item-icon>
            <v-list-item-title>โปรไฟล์</v-list-item-title>
          </v-list-item>
          <v-list-item @click="() => {}">
            <v-list-item-icon><v-icon>mdi-cog</v-icon></v-list-item-icon>
            <v-list-item-title>ตั้งค่า</v-list-item-title>
          </v-list-item>
          <v-divider></v-divider>
          <v-list-item @click="() => {}">
            <v-list-item-icon><v-icon>mdi-logout</v-icon></v-list-item-icon>
            <v-list-item-title>ออกจากระบบ</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <!-- Main Content Area -->
    <v-main class="main-content-area-new">
      <v-container fluid class="pa-8 content-container-new">
        <!-- Nuxt component will be rendered here -->
        <nuxt />
        <!-- Placeholder content for demonstration -->
        <v-card class="placeholder-card-new pa-8 rounded-xl elevation-6">
          <v-icon size="72" class="mb-4 primary--text text--lighten-2">mdi-rocket-launch-outline</v-icon>
          <h2 class="text-h4 font-weight-light mb-4 primary--text">ยินดีต้อนรับสู่ {{ title }}</h2>
          <p class="text-body-1 grey--text text--lighten-2">
            นี่คือพื้นที่หลักสำหรับเนื้อหาแอปพลิเคชันของคุณ
            <br>
            ใช้เมนูด้านซ้ายเพื่อสำรวจส่วนต่างๆ
          </p>
          <v-btn color="primary" class="mt-6 font-weight-bold" rounded>
            <v-icon left>mdi-chevron-right</v-icon>
            เริ่มต้นใช้งาน
          </v-btn>
        </v-card>
      </v-container>
    </v-main>

    <!-- Footer -->
    <v-footer
      app
      class="justify-center py-4 footer-custom-new"
      color="#1F2636"
    >
      <span class="white--text font-weight-light">&copy; {{ new Date().getFullYear() }} {{ title }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      items: [
        {
          icon: 'mdi-home-outline',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-category-outline',
          title: 'Inspire',
          to: '/inspire'
        },
        {
          icon: 'mdi-chart-bar-stacked',
          title: 'Sing UP',
          to: '/signup'
        }
      ],
      miniVariant: false,
      title: 'DEWGASOHOL Dashboard' // ชื่อแอปพลิเคชัน
    }
  }
}
</script>

<style scoped>
/* Global dark theme base */
.v-application.theme--dark {
  background-color: #1A1A1A; /* Darker overall background */
}

/* Navigation Drawer Customization */
.drawer-bg-custom {
  background: linear-gradient(135deg, #1F2636 0%, #171D28 100%); /* Deep blue-gray gradient */
  box-shadow: 0px 8px 20px rgba(0, 0, 0, 0.4); /* More pronounced shadow */
}

.user-profile-section {
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  padding: 20px 16px !important; /* Force padding */
}

.user-profile-section .user-name {
  color: #FFAB00; /* Accent color for name */
}

.user-profile-section .v-list-item-avatar img {
  border: 2px solid #FFAB00; /* Accent border for avatar */
  box-shadow: 0 0 10px rgba(255, 171, 0, 0.3); /* Glow effect */
}

.list-item-active-custom {
  background-color: rgba(255, 171, 0, 0.15); /* Accent color with transparency */
  border-left: 5px solid #FFAB00; /* Stronger accent border */
  color: #FFAB00 !important;
  font-weight: 600; /* Bolder text for active items */
}

.list-item-active-custom .v-icon {
  color: #FFAB00 !important;
}

/* App Bar Customization */
.app-bar-custom {
  background-color: #1F2636 !important; /* Match drawer top color */
  border-bottom: 1px solid rgba(255, 255, 255, 0.08); /* Subtle border */
}

.app-bar-title {
  font-family: 'Inter', sans-serif;
  font-weight: 700; /* Bolder title */
  font-size: 1.8rem;
  letter-spacing: 0.08em; /* More prominent letter spacing */
  color: #E0E0E0; /* Slightly off-white for title */
}

.user-avatar-btn {
  transition: transform 0.2s ease-in-out;
}
.user-avatar-btn:hover {
  transform: scale(1.1);
}

.user-menu-list {
  background-color: #283347 !important; /* Darker background for dropdown */
  border-radius: 8px;
}
.user-menu-list .v-list-item {
  color: white;
}
.user-menu-list .v-list-item:hover {
  background-color: rgba(255, 171, 0, 0.1);
  color: #FFAB00;
}
.user-menu-list .v-list-item:hover .v-icon {
  color: #FFAB00;
}

/* Main Content Area Customization */
.main-content-area-new {
  background: #1A1A1A; /* Consistent dark background */
  padding: 30px; /* More padding around the container */
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: calc(100vh - 64px - 52px); /* Maintain calculation */
}

.content-container-new {
  background-color: #283347 !important; /* Lighter blue-gray for content card */
  border-radius: 20px; /* Even rounder corners */
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.5); /* Stronger shadow */
  min-height: 550px; /* Slightly taller minimum height */
  padding: 40px !important; /* More internal padding */
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

/* Placeholder card style */
.placeholder-card-new {
  background-color: rgba(30, 40, 50, 0.6) !important; /* Slightly transparent dark blue */
  border: 1px solid rgba(255, 171, 0, 0.3); /* Accent border */
  max-width: 550px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
}

/* Footer Customization */
.footer-custom-new {
  background-color: #1F2636 !important; /* Match app bar */
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

/* Responsive adjustments */
@media (max-width: 960px) {
  .app-bar-title {
    font-size: 1.5rem;
  }
  .content-container-new {
    padding: 30px !important;
  }
}

@media (max-width: 600px) {
  .app-bar-title {
    font-size: 1.3rem;
  }
  .main-content-area-new {
    padding: 15px;
  }
  .content-container-new {
    padding: 25px !important;
    border-radius: 15px;
    min-height: 400px;
  }
  .placeholder-card-new {
    padding: 25px;
  }
  .user-profile-section {
    padding: 15px !important;
  }
  .user-profile-section .v-list-item-avatar {
    margin-right: 10px !important;
  }
}
</style>
