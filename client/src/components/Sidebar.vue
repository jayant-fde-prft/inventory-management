<template>
  <aside class="app-sidebar">
    <div class="brand">
      <h1>{{ t('nav.companyName') }}</h1>
      <span class="subtitle">{{ t('nav.subtitle') }}</span>
    </div>

    <nav class="nav-list">
      <router-link to="/" :class="{ active: $route.path === '/' }">
        <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
          <path d="M2 8L9 2L16 8" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M4 7V15C4 15.5523 4.44772 16 5 16H13C13.5523 16 14 15.5523 14 15V7" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        {{ t('nav.overview') }}
      </router-link>

      <router-link to="/inventory" :class="{ active: $route.path === '/inventory' }">
        <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
          <path d="M2 5.5L9 2L16 5.5L9 9L2 5.5Z" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M2 5.5V12.5L9 16L16 12.5V5.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M9 9V16" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
        {{ t('nav.inventory') }}
      </router-link>

      <router-link to="/orders" :class="{ active: $route.path === '/orders' }">
        <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
          <path d="M5 3H13C13.5523 3 14 3.44772 14 4V15C14 15.5523 13.5523 16 13 16H5C4.44772 16 4 15.5523 4 15V4C4 3.44772 4.44772 3 5 3Z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/>
          <path d="M7 2H11V4H7V2Z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/>
          <path d="M6.5 8H11.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <path d="M6.5 11H11.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
        {{ t('nav.orders') }}
      </router-link>

      <router-link to="/spending" :class="{ active: $route.path === '/spending' }">
        <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
          <path d="M2 15L7 9L11 12L16 5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M11.5 5H16V9.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        {{ t('nav.finance') }}
      </router-link>

      <router-link to="/demand" :class="{ active: $route.path === '/demand' }">
        <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
          <path d="M3 15V3" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <path d="M3 15H16" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <path d="M6 12V9" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <path d="M9.5 12V6" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <path d="M13 12V10.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
        {{ t('nav.demandForecast') }}
      </router-link>

      <router-link to="/reports" :class="{ active: $route.path === '/reports' }">
        <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
          <path d="M5 2H11L14 5V15C14 15.5523 13.5523 16 13 16H5C4.44772 16 4 15.5523 4 15V3C4 2.44772 4.44772 2 5 2Z" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/>
          <path d="M11 2V5H14" stroke="currentColor" stroke-width="1.5" stroke-linejoin="round"/>
          <path d="M6.5 9H11.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
          <path d="M6.5 12H11.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round"/>
        </svg>
        {{ t('nav.reports') }}
      </router-link>
    </nav>

    <div class="sidebar-footer">
      <LanguageSwitcher />
      <ProfileMenu
        @show-profile-details="$emit('show-profile-details')"
        @show-tasks="$emit('show-tasks')"
      />
    </div>
  </aside>
</template>

<script>
import { useI18n } from '../composables/useI18n'
import ProfileMenu from './ProfileMenu.vue'
import LanguageSwitcher from './LanguageSwitcher.vue'

export default {
  name: 'Sidebar',
  components: {
    ProfileMenu,
    LanguageSwitcher
  },
  emits: ['show-profile-details', 'show-tasks'],
  setup() {
    const { t } = useI18n()

    return {
      t
    }
  }
}
</script>

<style scoped>
.app-sidebar {
  position: fixed;
  left: 0;
  top: 0;
  width: 240px;
  height: 100vh;
  display: flex;
  flex-direction: column;
  background: #ffffff;
  border-right: 1px solid #e2e8f0;
  padding: 1.5rem 1rem;
  z-index: 100;
}

.brand {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
  padding: 0 0.5rem;
  margin-bottom: 1.5rem;
}

.brand h1 {
  font-size: 1.125rem;
  font-weight: 700;
  color: #0f172a;
  letter-spacing: -0.025em;
}

.brand .subtitle {
  font-size: 0.75rem;
  color: #64748b;
  font-weight: 400;
}

.nav-list {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.nav-list a {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.625rem 0.75rem;
  color: #64748b;
  text-decoration: none;
  font-weight: 500;
  font-size: 0.875rem;
  border-radius: 6px;
  transition: all 0.2s ease;
  position: relative;
}

.nav-list a svg {
  flex-shrink: 0;
}

.nav-list a:hover {
  color: #0f172a;
  background: #f1f5f9;
}

.nav-list a.active {
  color: #2563eb;
  background: #eff6ff;
}

.nav-list a.active::before {
  content: '';
  position: absolute;
  left: -1rem;
  top: 0;
  bottom: 0;
  width: 3px;
  background: #2563eb;
  border-radius: 0 3px 3px 0;
}

.sidebar-footer {
  margin-top: auto;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  padding-top: 1rem;
}
</style>
