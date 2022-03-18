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
        title: 'Toasts',
        onSelect: () => replace(`/toasts/info`),
      },
      {
        id: 'examples',
        title: 'Examples',
        onSelect: () => replace(`/toasts/examples`),
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
          <Typography>Toasts info</Typography>
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[1].id}
      <Card cardId={$view.cards[1].id}>
        <CardHeader />
        <CardContent>
          <Typography>Show a single toast.</Typography>
          <Button
            title="Show One"
            color={Color.Primary}
            navi={{
              itemId: `btn1`,
              onSelect: () => Onyx.toaster.show({ title: 'Sample toast message' }),
            }}
          />
          <Typography
            >Only one toast can be visible at a time. What happens if you call toast multiple times
            in a row? They get queued and displayed in the order in which they were called.
          </Typography>
          <Button
            title="Show Three"
            color={Color.Primary}
            navi={{
              itemId: `btn2`,
              onSelect: () => {
                Onyx.toaster.show({ title: 'Sample toast message 1' });
                Onyx.toaster.show({ title: 'Sample toast message 2' });
                Onyx.toaster.show({ title: 'Sample toast message 3' });
              },
            }}
          />
        </CardContent>
      </Card>
    {/if}
  </ViewContent>
</View>
