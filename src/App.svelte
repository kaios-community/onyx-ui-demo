<script lang="ts">
  import { keys } from 'onyx-ui/actions';
  import Dashboard from 'onyx-ui/components/app/Dashboard.svelte';
  import OnyxApp from 'onyx-ui/components/app/OnyxApp.svelte';
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
</script>

<OnyxApp baseSettings={settings}>
  <AppMenu slot="app-menu" />
  <Router {routes} />
  {#if false}
    <Dashboard slot="dashboard">Hello</Dashboard>
  {/if}
</OnyxApp>
<div
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
/>
