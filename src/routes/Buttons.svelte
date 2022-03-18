<script lang="ts">
  import Button from 'onyx-ui/components/buttons/Button.svelte';
  import Card from 'onyx-ui/components/card/Card.svelte';
  import CardContent from 'onyx-ui/components/card/CardContent.svelte';
  import CardHeader from 'onyx-ui/components/card/CardHeader.svelte';
  import Typography from 'onyx-ui/components/Typography.svelte';
  import View from 'onyx-ui/components/view/View.svelte';
  import ViewContent from 'onyx-ui/components/view/ViewContent.svelte';
  import { Color, DataStatus } from 'onyx-ui/enums';
  import { registerView, updateView, view } from 'onyx-ui/stores/view';
  import { onMount } from 'svelte';
  import MdContentCopy from 'svelte-icons/md/MdContentCopy.svelte';
  import { replace } from 'svelte-spa-router';

  export let params: { cardId: string };

  registerView({
    cards: [
      {
        id: 'info',
        title: 'Buttons',
        onSelect: () => replace(`/buttons/info`),
      },
      {
        id: 'text',
        title: 'Text Buttons',
        onSelect: () => replace(`/buttons/text`),
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
          <Typography>Buttons info</Typography>
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[1].id}
      <Card cardId={$view.cards[1].id}>
        <CardHeader />
        <CardContent>
          <Button
            title="Primary Button"
            color={Color.Primary}
            navi={{
              itemId: `primary`,
              onSelect: async () => console.log('primary'),
            }}
          />
          <Button
            title="Secondary Button"
            color={Color.Secondary}
            navi={{
              itemId: `secondary`,
              onSelect: async () => console.log('secondary'),
            }}
          />
          <Button
            title="Accent Button"
            color={Color.Accent}
            navi={{
              itemId: `accent`,
              onSelect: async () => console.log('accent'),
            }}
          />
          <Button
            icon={MdContentCopy}
            title="Button With Icon"
            navi={{
              itemId: `withIcon`,
              onSelect: async () => console.log('withIcon'),
            }}
          />
          <Button
            title="Disabled Button"
            disabled
            color={Color.Primary}
            navi={{
              itemId: `disabled`,
              onSelect: async () => console.log('disabled'),
            }}
          />
        </CardContent>
      </Card>
    {/if}
  </ViewContent>
</View>
