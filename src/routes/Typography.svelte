<script lang="ts">
  import { onMount } from 'svelte';
  import Card from 'onyx-ui/components/card/Card.svelte';
  import CardContent from 'onyx-ui/components/card/CardContent.svelte';
  import CardHeader from 'onyx-ui/components/card/CardHeader.svelte';
  import Typography from 'onyx-ui/components/Typography.svelte';
  import View from 'onyx-ui/components/view/View.svelte';
  import ViewContent from 'onyx-ui/components/view/ViewContent.svelte';
  import { DataStatus } from 'onyx-ui/enums';
  import { registerView, updateView } from 'onyx-ui/stores/view';

  registerView({});

  onMount(async () => {
    updateView({ dataStatus: DataStatus.Loaded });
  });
</script>

<View>
  <ViewContent>
    <Card>
      <CardHeader title="Typography" />
      <CardContent>
        <Typography type="titleSmall">Colors</Typography>
        <Typography color="primary">Here's a small bit of primary text</Typography>
        <Typography color="secondary">Here's a small bit of secondary text</Typography>
        <Typography color="accent">Here's a small bit of accent text</Typography>

        <Typography type="titleSmall">Sizes</Typography>
        <Typography type="caption">Here's a small bit of caption text</Typography>
        <Typography type="body">Here's a small bit of body text</Typography>
        <Typography type="bodyLarge">Here's a small bit of large body text</Typography>
        <Typography type="titleSmall">Title Small</Typography>
        <Typography type="title">Title</Typography>
        <Typography type="titleLarge">Title Large</Typography>

        <Typography type="titleSmall">Other</Typography>
        <Typography type="body">
          You can even use the typography component{' '}
          <Typography display="inline" padding="none" color="accent">inline</Typography>{' '}
          to style certain text{' '}
          <Typography display="inline" padding="none" decoration="underline">
            differently
          </Typography>
          .
        </Typography>
      </CardContent>
    </Card>
  </ViewContent>
</View>
