<script lang="ts">
  import { onMount } from 'svelte';
  import { replace } from 'svelte-spa-router';
  import Card from 'onyx-ui/components/card/Card.svelte';
  import CardContent from 'onyx-ui/components/card/CardContent.svelte';
  import CardHeader from 'onyx-ui/components/card/CardHeader.svelte';
  import ListItem from 'onyx-ui/components/list/ListItem.svelte';
  import Typography from 'onyx-ui/components/Typography.svelte';
  import View from 'onyx-ui/components/view/View.svelte';
  import ViewContent from 'onyx-ui/components/view/ViewContent.svelte';
  import { DataStatus } from 'onyx-ui/enums';
  import { registerView, updateView, view } from 'onyx-ui/stores/view';
  import { delay } from 'onyx-ui/utils/delay';

  export let params: { cardId: string };

  registerView({
    cards: [
      { id: 'info', title: 'Context Menus', onSelect: () => replace(`/contextMenus/info`) },
      { id: 'examples', title: 'Examples', onSelect: () => replace(`/contextMenus/examples`) },
    ],
    activeCardId: params.cardId ?? 'info',
  });

  onMount(async () => {
    updateView({ dataStatus: DataStatus.Loaded });
  });

  let items = new Array(10).fill(null);
</script>

<View>
  <ViewContent>
    {#if params.cardId === $view.cards[0].id}
      <Card cardId={$view.cards[0].id}>
        <CardHeader />
        <CardContent>
          <Typography>Context menu info</Typography>
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[1].id}
      <Card cardId={$view.cards[1].id}>
        <CardHeader />
        <CardContent>
          {#each items as item, i}
            <ListItem
              primaryText={`Primary Text ${i + 1}`}
              secondaryText={`Secondary Text`}
              navi={{
                itemId: `${i + 1}`,
                onSelect: () => console.log(i + 1, 'select'),
              }}
              contextMenu={{
                title: `Primary Text ${i + 1}`,
                items: [
                  {
                    label: 'Context Menu Item 1',
                    workingLabel: 'Working...',
                    onSelect: async () => {
                      console.log('context menu item 1');
                      await delay(1000);
                    },
                  },
                  {
                    label: 'Context Menu Item 2',
                    onSelect: async () => {
                      console.log('context menu item 2');
                      await delay(1000);
                    },
                  },
                  {
                    label: 'Context Menu Item 3',
                    onSelect: () => console.log('context menu item 3'),
                  },
                ],
              }}
            />
          {/each}
        </CardContent>
      </Card>
    {/if}
  </ViewContent>
</View>
