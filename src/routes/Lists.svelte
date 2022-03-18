<script lang="ts">
  import Card from 'onyx-ui/components/card/Card.svelte';
  import CardContent from 'onyx-ui/components/card/CardContent.svelte';
  import CardHeader from 'onyx-ui/components/card/CardHeader.svelte';
  import ListItem from 'onyx-ui/components/list/ListItem.svelte';
  import Typography from 'onyx-ui/components/Typography.svelte';
  import View from 'onyx-ui/components/view/View.svelte';
  import ViewContent from 'onyx-ui/components/view/ViewContent.svelte';
  import { DataStatus } from 'onyx-ui/enums';
  import { registerView, updateView, view } from 'onyx-ui/stores/view';
  import { getShortcutFromIndex } from 'onyx-ui/utils/getShortcutFromIndex';
  import { onMount } from 'svelte';
  import { replace } from 'svelte-spa-router';

  export let params: { cardId: string };

  registerView({
    cards: [
      { id: 'info', title: 'Lists', onSelect: () => replace(`/lists/info`) },
      { id: 'single', title: 'Single Line List', onSelect: () => replace(`/lists/single`) },
      { id: 'two', title: 'Two Line List', onSelect: () => replace(`/lists/two`) },
      { id: 'three', title: 'Three Line List', onSelect: () => replace(`/lists/three`) },
      {
        id: 'shortcuts',
        title: 'List With Shortcuts',
        onSelect: () => replace(`/lists/shortcuts`),
      },
      { id: 'images', title: 'List With Images', onSelect: () => replace(`/lists/images`) },
    ],
    activeCardId: params.cardId ?? 'info',
  });

  let items = new Array(10).fill(null);

  onMount(async () => {
    updateView({ dataStatus: DataStatus.Loaded });
  });
</script>

<View>
  <ViewContent>
    {#if params.cardId === $view.cards[0].id}
      <Card cardId={$view.cards[0].id}>
        <CardHeader />
        <CardContent>
          <Typography>List info</Typography>
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[1].id}
      <Card cardId={$view.cards[1].id}>
        <CardHeader />
        <CardContent>
          {#each items as item, i}
            <ListItem
              primaryText={`Primary Text ${i + 1}`}
              navi={{
                itemId: `${i + 1}`,
              }}
            />
          {/each}
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[2].id}
      <Card cardId={$view.cards[2].id}>
        <CardHeader />
        <CardContent>
          {#each items as item, i}
            <ListItem
              primaryText={`Primary Text ${i + 1}`}
              secondaryText="Secondary text"
              navi={{
                itemId: `${i + 1}`,
              }}
            />
          {/each}
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[3].id}
      <Card cardId={$view.cards[3].id}>
        <CardHeader />
        <CardContent>
          {#each items as item, i}
            <ListItem
              primaryText={`Primary Text ${i + 1}`}
              secondaryText="Secondary text"
              accentText="Accent Text"
              navi={{
                itemId: `${i + 1}`,
              }}
            />
          {/each}
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[4].id}
      <Card cardId={$view.cards[4].id}>
        <CardHeader />
        <CardContent>
          {#each items as item, i}
            <ListItem
              primaryText={`Primary Text ${i + 1}`}
              secondaryText="Secondary text"
              navi={{
                itemId: `${i + 1}`,
                shortcutKey: getShortcutFromIndex(i),
              }}
            />
          {/each}
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[5].id}
      <Card cardId={$view.cards[5].id}>
        <CardHeader />
        <CardContent>
          {#each items as item, i}
            <ListItem
              imageUrl="https://place-hold.it/32x32&text="
              primaryText={`Primary Text ${i + 1}`}
              secondaryText="Secondary text"
              navi={{
                itemId: `${i + 1}`,
                shortcutKey: getShortcutFromIndex(i),
              }}
            />
          {/each}
        </CardContent>
      </Card>
    {/if}
  </ViewContent>
</View>
