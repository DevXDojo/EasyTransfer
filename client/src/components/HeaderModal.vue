<script setup lang="ts">
import { ref } from 'vue'
import SettingsModal from '@/components/SettingsModal.vue'
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiCog, mdiGithub } from '@mdi/js'
import { useI18n } from 'vue-i18n'

const { t } = useI18n()
const showSettings = ref<boolean>(false)
const toggleSettings = (): void => {
  showSettings.value = !showSettings.value
}
</script>

<template>
  <header>
    <div class="header-cluster">
      <div class="logo-cluster">
        <img src="../../favicon.png" alt="EasyTransfer Logo" />
      </div>
      <div class="link-cluster">
        <button class="link-item shadow" @click="toggleSettings">
          <SvgIcon type="mdi" :path="mdiCog" size="1.5rem" /><span
            class="text"
            >{{ t('header.settings') }}</span
          >
        </button>
        <a
          href="https://github.com/DevXDojo/EasyTransfer"
          class="link-item shadow github"
        >
          <SvgIcon type="mdi" :path="mdiGithub" size="1.5rem" /><span
            class="text"
            >{{ t('header.starOnGitHub') }}</span
          >
        </a>
      </div>
    </div>
  </header>
  <SettingsModal v-if="showSettings" @close="toggleSettings" />
</template>

<style scoped lang="scss">
header {
  display: grid;
  place-items: center;

  position: sticky;
  top: 0;
  width: 100%;
  z-index: 1000;
  margin-bottom: 1rem;

  background-color: var(--primary-color);
  color: var(--light-color);

  font-family: var(--normal-font-family);

  transition: all 0.3s ease-in-out;

  .header-cluster {
    width: calc(min(100%, 125rem));
    padding: 1rem 1rem;

    display: flex;
    justify-content: space-between;
    align-items: center;

    transition: all 0.3s ease-in-out;
  }

  .logo-cluster {
    display: flex;
    align-items: center;

    transition: all 0.3s ease-in-out;

    img {
      height: 3rem;
    }
  }

  .link-cluster {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.8rem;

    transition: all 0.3s ease-in-out;

    @media (max-width: 425px) {
      gap: 0.4rem;
    }
  }

  .link-item {
    border: none;
    outline: none;
    background: none;

    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;

    padding: 0.5rem 1rem;

    color: var(--primary-color);
    background-color: var(--primary-light-color);

    border-radius: var(--border-radius);

    text-decoration: none;
    line-height: 1rem;

    cursor: pointer;

    transition:
      padding 0.3s ease-in-out,
      color 0.1s ease-in-out,
      background-color 0.1s ease-in-out;

    &.github {
      color: var(--dark-color);
      background-color: var(--gold-color);
    }

    .mdi {
      font-size: 1.5rem;
      line-height: 1.5rem;
    }

    .text {
      font-family: var(--normal-font-family);
      font-size: 1rem;
    }

    @media (hover: hover) {
      &:hover {
        color: var(--primary-light-color);
        background-color: var(--primary-semi-dark-color);

        &.github {
          color: var(--dark-color);
          background-color: var(--gold-light-color);
        }
      }
    }

    @media (max-width: 768px) {
      padding: 0.5rem;

      .text {
        display: none;
      }
    }
  }

  &.blur.shadow {
    --blur-effect: blur(10px);

    background-color: var(--light-blur-color);

    .header-cluster {
      padding: 0.5rem 1rem;

      .logo-cluster {
        gap: 0.3rem;

        svg {
          fill: var(--primary-color);
          width: 2.5rem;
          height: 2.5rem;
        }

        .logo-text {
          * {
            color: var(--primary-color);
          }

          h1 {
            font-size: 1.5rem;
            line-height: 1.5rem;
          }

          span {
            font-size: 0.8rem;
          }

          p {
            font-size: 0.8rem;
          }
        }
      }
    }

    .link-cluster {
      gap: 0.6rem;

      @media (max-width: 425px) {
        gap: 0.3rem;
      }
    }

    .link-item {
      padding: 0.3rem 0.8rem;

      @media (max-width: 768px) {
        padding: 0.3rem;
      }
    }
  }
}
</style>
