<script lang="ts">
  import Dashboard from 'onyx-ui/components/app/Dashboard.svelte';
  import OnyxApp from 'onyx-ui/components/app/OnyxApp.svelte';
  import { Priority } from 'onyx-ui/enums';
  import { KeyManager, Onyx } from 'onyx-ui/services';
  import { onMount } from 'svelte';
  import Router, { location, pop } from 'svelte-spa-router';
  import AppMenu from './components/AppMenu.svelte';
  import AppSettings from './routes/AppSettings.svelte';
  import Cards from './routes/Cards.svelte';
  import ContextMenus from './routes/ContextMenus.svelte';
  import Form from './routes/Form.svelte';
  import Home from './routes/Home.svelte';
  import Lists from './routes/Lists.svelte';
  import Redirect from './routes/Redirect.svelte';
  import Typography from './routes/Typography.svelte';
  import { settings } from './stores/settings';

  const routes = {
    '/': Home,
    '/cards/:cardId': Cards,
    '/typography/:cardId': Typography,
    '/lists/:cardId': Lists,
    '/contextMenus/:cardId': ContextMenus,
    '/forms/:cardId': Form,
    '/settings/:cardId': AppSettings,
    '*': Redirect,
  };

  const keyMan = KeyManager.subscribe(
    {
      onBackspace: () => {
        // If on the main screen, let KaiOS minimize the app
        if ($location === '/') {
          console.log('exit app');
          return false;
        }

        pop();
        return true;
      },
    },
    Priority.Low
  );

  $: Onyx.settings.update($settings);

  onMount(() => {
    // Onyx.dialog.show({
    //   title: 'Dialog Title',
    //   body: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent facilisis fringilla ligula, vel porta sem rhoncus id.',
    //   actions: {
    //     left: { label: 'Action1', fn: () => console.log('Action1') },
    //     center: { label: 'Action2', fn: () => console.log('Action2') },
    //     right: { label: 'Action3', fn: () => console.log('Action3') },
    //   },
    // });
    // Onyx.alert.show({
    //   title: 'Alert Title',
    //   body: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent facilisis fringilla ligula, vel porta sem rhoncus id.',
    // });
    // setTimeout(() => {
    // Onyx.toaster.show({ title: 'Test toast message 2' });
    // Onyx.toaster.show({
    //   title:
    //     'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent facilisis fringilla ligula, vel porta sem rhoncus id.',
    // });
    // Onyx.toaster.show({ title: 'Test toast message 3' });
    // }, 0);
  });
</script>

<OnyxApp>
  <AppMenu slot="app-menu" />
  <Router {routes} />
  {#if false}
    <Dashboard slot="dashboard">Hello</Dashboard>
  {/if}
</OnyxApp>
<!-- <div
  use:keys={{
    onBackspace: () => {
      // If on the main screen, let KaiOS minimize the app
      if ($location === '/') {
        console.log('exit app');
        return false;
      }

      pop();
      return true;
    },
  }}
/> -->
