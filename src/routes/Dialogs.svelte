<script lang="ts">
  import Button from 'onyx-ui/components/buttons/Button.svelte';
  import Card from 'onyx-ui/components/card/Card.svelte';
  import CardContent from 'onyx-ui/components/card/CardContent.svelte';
  import CardHeader from 'onyx-ui/components/card/CardHeader.svelte';
  import Typography from 'onyx-ui/components/Typography.svelte';
  import View from 'onyx-ui/components/view/View.svelte';
  import ViewContent from 'onyx-ui/components/view/ViewContent.svelte';
  import { Color, DataStatus } from 'onyx-ui/enums';
  import { Onyx } from 'onyx-ui/services';
  import { registerView, updateView, view } from 'onyx-ui/stores/view';
  import { onMount } from 'svelte';
  import { replace } from 'svelte-spa-router';

  export let params: { cardId: string };

  registerView({
    cards: [
      {
        id: 'info',
        title: 'Dialogs',
        onSelect: () => replace(`/dialogs/info`),
      },
      {
        id: 'examples',
        title: 'Dialogs',
        onSelect: () => replace(`/dialogs/examples`),
      },
    ],
    activeCardId: params.cardId ?? 'info',
  });

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
          <Typography>Dialogs info</Typography>
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[1].id}
      <Card cardId={$view.cards[1].id}>
        <CardHeader />
        <CardContent>
          <Typography
            >An example of a dialog that has a title, body, and three different actions. This
            component is used to prompt the user for a choice. If can also be used as a simple alert
            with customizable key functions.</Typography
          >
          <Button
            title="Open"
            color={Color.Primary}
            navi={{
              itemId: `alert1`,
              onSelect: () =>
                Onyx.dialog.show({
                  title: 'Dialog Title',
                  body: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent facilisis fringilla ligula, vel porta sem rhoncus id.',
                  actions: {
                    left: { label: 'Action1', fn: () => console.log('Action1') },
                    center: { label: 'Action2', fn: () => console.log('Action2') },
                    right: { label: 'Action3', fn: () => console.log('Action3') },
                  },
                }),
            }}
          />
        </CardContent>
      </Card>
    {/if}
  </ViewContent>
</View>
