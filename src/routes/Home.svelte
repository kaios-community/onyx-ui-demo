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
      <CardHeader title="Home" />
      <CardContent>
        <Typography>Hello.</Typography>
        <Typography>
          Welcome! OnyxUI is a UI component library for KaiOS. This app serves as a demo of all the
          different features and components. Press{' '}
          <Typography display="inline" color="accent" padding="none">SoftLeft</Typography>{' '}
          to get started.
        </Typography>
      </CardContent>
    </Card>
  </ViewContent>
</View>
