<template>
  <div
    class="app-content content"
    :class="[{'show-overlay': $store.state.app.shallShowOverlay}, $route.meta.contentClass]"
  >
    <div class="content-overlay" />
    <div class="header-navbar-shadow" />
    <div style="display:flex;align-items:center;width:100vw;background-color:#FA5252;color:black;font-weight:bold;">
      <div style="display:flex;align-items:center;justify-content:center;width:100%;">
        TESTNET
      </div>
    </div>
    <transition
      :name="routerTransition"
      mode="out-in"
    >
      <div
        class="content-area-wrapper"
        :class="contentWidth === 'boxed' ? 'container p-0' : null"
      >
        <slot name="breadcrumb">
          <app-breadcrumb />
        </slot>
        <portal-target
          name="content-renderer-sidebar-left"
          slim
        />
        <div class="content-right">
          <div class="content-wrapper">
            <div class="content-body">
              <slot />
            </div>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
import AppBreadcrumb from '@core/layouts/components/AppBreadcrumb.vue'
import useAppConfig from '@core/app-config/useAppConfig'

export default {
  components: {
    AppBreadcrumb,
  },
  setup() {
    const { routerTransition, contentWidth } = useAppConfig()

    return {
      routerTransition, contentWidth,
    }
  },
}
</script>

<style>

</style>
