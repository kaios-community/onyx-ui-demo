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
        title: 'Alerts',
        onSelect: () => replace(`/alerts/info`),
      },
      {
        id: 'examples',
        title: 'Examples',
        onSelect: () => replace(`/alerts/examples`),
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
          <Typography>Popups info</Typography>
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[1].id}
      <Card cardId={$view.cards[1].id}>
        <CardHeader />
        <CardContent>
          <Typography
            >An alert with only a title, but try to always include a body. If you're looking for
            something simpler, check out Toaster.</Typography
          >
          <Button
            title="Open"
            color={Color.Primary}
            navi={{
              itemId: `alert1`,
              onSelect: () =>
                Onyx.alert.show({
                  title: 'Alert Title',
                }),
            }}
          />
          <Typography
            >An alert with a title and short body. The content is short enough so that theree is no
            scrolling.</Typography
          >
          <Button
            title="Open"
            color={Color.Primary}
            navi={{
              itemId: `alert2`,
              onSelect: () =>
                Onyx.alert.show({
                  title: 'Alert Title',
                  body: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent facilisis fringilla ligula, vel porta sem rhoncus id.',
                }),
            }}
          />
          <Typography
            >An alert with a title and long body. This example uses a very long body to demonstrate
            scrolling. You probably shouldn't have a body this long.</Typography
          >
          <Button
            title="Open"
            color={Color.Primary}
            navi={{
              itemId: `alert3`,
              onSelect: () =>
                Onyx.alert.show({
                  title: 'Alert Title',
                  body: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent facilisis fringilla ligula, vel porta sem rhoncus id. Integer ac dolor facilisis, aliquam tortor vitae, volutpat augue. Nulla urna sem, ullamcorper ac purus nec, gravida dapibus enim. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Sed feugiat ultricies mauris vel rhoncus. Donec at nunc erat. Nulla auctor nibh quis justo fermentum tempor. Sed viverra risus ut elit scelerisque blandit interdum auctor ligula. Maecenas id est eleifend, fringilla arcu ut, dapibus purus. Maecenas accumsan, turpis in efficitur rhoncus, leo nibh lobortis turpis, nec lacinia augue libero vitae sapien. Sed ultrices velit eros, non vulputate purus consectetur at. Quisque elementum orci nisl, a mattis nunc porta sit amet. Aenean egestas, nisl nec ornare lacinia, ex odio venenatis dui, maximus finibus lectus lorem eget purus. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Curabitur id nunc eget libero mollis vestibulum. Sed eu magna et risus faucibus consequat quis vel erat.',
                }),
            }}
          />
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[2].id}
      <Card cardId={$view.cards[2].id}>
        <CardHeader />
        <CardContent>
          <Typography type="titleSmall">Dialog 1</Typography>
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
