<script lang="ts">
  import { onMount } from 'svelte';
  import Card from 'onyx-ui/components/card/Card.svelte';
  import CardContent from 'onyx-ui/components/card/CardContent.svelte';
  import CardHeader from 'onyx-ui/components/card/CardHeader.svelte';
  import Grid from 'onyx-ui/components/grid/Grid.svelte';
  import GridItem from 'onyx-ui/components/grid/GridItem.svelte';
  import ListItem from 'onyx-ui/components/list/ListItem.svelte';
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
        <Typography>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent facilisis fringilla
          ligula, vel porta sem rhoncus id. Integer ac dolor facilisis, aliquam tortor vitae,
          volutpat augue. Nulla urna sem, ullamcorper ac purus nec, gravida dapibus enim.
          Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis
          egestas. Sed feugiat ultricies mauris vel rhoncus. Donec at nunc erat. Nulla auctor nibh
          quis justo fermentum tempor. Sed viverra risus ut elit scelerisque blandit interdum auctor
          ligula. Maecenas id est eleifend, fringilla arcu ut, dapibus purus. Maecenas accumsan,
          turpis in efficitur rhoncus, leo nibh lobortis turpis, nec lacinia augue libero vitae
          sapien. Sed ultrices velit eros, non vulputate purus consectetur at. Quisque elementum
          orci nisl, a mattis nunc porta sit amet. Aenean egestas, nisl nec ornare lacinia, ex odio
          venenatis dui, maximus finibus lectus lorem eget purus. Orci varius natoque penatibus et
          magnis dis parturient montes, nascetur ridiculus mus. Curabitur id nunc eget libero mollis
          vestibulum. Sed eu magna et risus faucibus consequat quis vel erat.
        </Typography>
        <Grid columns={2}>
          <GridItem navi={{ itemId: 'grid-1' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid0' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <ListItem primaryText="List Item" navi={{ itemId: 'list1' }} />
        <ListItem primaryText="List Item" navi={{ itemId: 'list2' }} />
        <ListItem primaryText="List Item" navi={{ itemId: 'list3' }} />
        <Grid columns={3}>
          <GridItem navi={{ itemId: 'grid1' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid2' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid3' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <Grid columns={2}>
          <GridItem navi={{ itemId: 'grid4' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid5' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <Grid columns={3}>
          <GridItem navi={{ itemId: 'grid6' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid7' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid8' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <ListItem primaryText="List Item" navi={{ itemId: 'list4' }} />
        <ListItem primaryText="List Item" navi={{ itemId: 'list6' }} />
        <Grid columns={3}>
          <GridItem navi={{ itemId: 'grid9' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid10' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'gri119' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <Typography>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent facilisis fringilla
          ligula, vel porta sem rhoncus id. Integer ac dolor facilisis, aliquam tortor vitae,
          volutpat augue. Nulla urna sem, ullamcorper ac purus nec, gravida dapibus enim.
          Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis
          egestas. Sed feugiat ultricies mauris vel rhoncus. Donec at nunc erat. Nulla auctor nibh
          quis justo fermentum tempor. Sed viverra risus ut elit scelerisque blandit interdum auctor
          ligula. Maecenas id est eleifend, fringilla arcu ut, dapibus purus. Maecenas accumsan,
          turpis in efficitur rhoncus, leo nibh lobortis turpis, nec lacinia augue libero vitae
          sapien. Sed ultrices velit eros, non vulputate purus consectetur at. Quisque elementum
          orci nisl, a mattis nunc porta sit amet. Aenean egestas, nisl nec ornare lacinia, ex odio
          venenatis dui, maximus finibus lectus lorem eget purus. Orci varius natoque penatibus et
          magnis dis parturient montes, nascetur ridiculus mus. Curabitur id nunc eget libero mollis
          vestibulum. Sed eu magna et risus faucibus consequat quis vel erat.
        </Typography>
        <Grid columns={2}>
          <GridItem navi={{ itemId: 'grid2-1' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid20' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <ListItem primaryText="List Item" navi={{ itemId: 'list21' }} />
        <ListItem primaryText="List Item" navi={{ itemId: 'list22' }} />
        <ListItem primaryText="List Item" navi={{ itemId: 'list23' }} />
        <Grid columns={3}>
          <GridItem navi={{ itemId: 'grid21' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid22' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid23' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <Grid columns={2}>
          <GridItem navi={{ itemId: 'grid24' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid25' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <Grid columns={3}>
          <GridItem navi={{ itemId: 'grid26' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid27' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid28' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <ListItem primaryText="List Item" navi={{ itemId: 'list24' }} />
        <ListItem primaryText="List Item" navi={{ itemId: 'list26' }} />
        <Grid columns={3}>
          <GridItem navi={{ itemId: 'grid29' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid210' }}><div class="grid-item">Grid Item</div></GridItem>
          <GridItem navi={{ itemId: 'grid211' }}><div class="grid-item">Grid Item</div></GridItem>
        </Grid>
        <Typography>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Praesent facilisis fringilla
          ligula, vel porta sem rhoncus id. Integer ac dolor facilisis, aliquam tortor vitae,
          volutpat augue. Nulla urna sem, ullamcorper ac purus nec, gravida dapibus enim.
          Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis
          egestas. Sed feugiat ultricies mauris vel rhoncus. Donec at nunc erat. Nulla auctor nibh
          quis justo fermentum tempor. Sed viverra risus ut elit scelerisque blandit interdum auctor
          ligula. Maecenas id est eleifend, fringilla arcu ut, dapibus purus. Maecenas accumsan,
          turpis in efficitur rhoncus, leo nibh lobortis turpis, nec lacinia augue libero vitae
          sapien. Sed ultrices velit eros, non vulputate purus consectetur at. Quisque elementum
          orci nisl, a mattis nunc porta sit amet. Aenean egestas, nisl nec ornare lacinia, ex odio
          venenatis dui, maximus finibus lectus lorem eget purus. Orci varius natoque penatibus et
          magnis dis parturient montes, nascetur ridiculus mus. Curabitur id nunc eget libero mollis
          vestibulum. Sed eu magna et risus faucibus consequat quis vel erat.
        </Typography>
        <!-- <Typography>Hello.</Typography>
        <Typography>
          Welcome! OnyxUI is a UI component library for KaiOS. This app serves as a demo of all the
          different features and components. Press{' '}
          <Typography display="inline" color="accent" padding="none">SoftLeft</Typography>{' '}
          to get started.
        </Typography> -->
      </CardContent>
    </Card>
  </ViewContent>
</View>

<style>
  .grid-item {
    border: 1px solid var(--divider-color);
    height: 30px;
  }
</style>
