<script lang="ts">
  import Card from 'onyx-ui/components/card/Card.svelte';
  import CardContent from 'onyx-ui/components/card/CardContent.svelte';
  import CardHeader from 'onyx-ui/components/card/CardHeader.svelte';
  import ColorPickerRow from 'onyx-ui/components/form/ColorPickerRow.svelte';
  import NumericRangeRow from 'onyx-ui/components/form/NumericRangeRow.svelte';
  import SelectRow from 'onyx-ui/components/form/SelectRow.svelte';
  import ToggleRow from 'onyx-ui/components/form/ToggleRow.svelte';
  import ListHeader from 'onyx-ui/components/list/ListHeader.svelte';
  import View from 'onyx-ui/components/view/View.svelte';
  import ViewContent from 'onyx-ui/components/view/ViewContent.svelte';
  import { Animations, DataStatus, Density, TextSize, TextWeight } from 'onyx-ui/enums';
  import { registerView, updateView, view } from 'onyx-ui/stores/view';
  import { onMount } from 'svelte';
  import { replace } from 'svelte-spa-router';
  import type { Settings } from '../models';
  import { settings } from '../stores/settings';
  import { themes } from '../themes';

  export let params: { cardId: string };

  registerView({
    cards: [
      {
        id: 'display',
        title: 'Display',
        onSelect: () => replace(`/settings/display`),
      },
      {
        id: 'features',
        title: 'Features',
        onSelect: () => replace(`/settings/features`),
      },
      {
        id: 'misc',
        title: 'Misc',
        onSelect: () => replace(`/settings/misc`),
      },
    ],
    activeCardId: params.cardId ?? 'display',
  });

  onMount(async () => {
    updateView({ dataStatus: DataStatus.Loaded });
  });

  function handleChange(key: keyof Settings, val: any) {
    settings.updateOne(key, val);

    if (key === 'themeId') {
      const theme = themes.find((a) => a.id === $settings.themeId) ?? themes[0];
      settings.update({
        accentColorH: theme.values.accentColorH,
        accentColorS: theme.values.accentColorS,
        accentColorL: theme.values.accentColorL,
        cardColorH: theme.values.cardColorH,
        cardColorS: theme.values.cardColorS,
        cardColorL: theme.values.cardColorL,
        textColorH: theme.values.textColorH,
        textColorS: theme.values.textColorS,
        textColorL: theme.values.textColorL,
        focusColorA: theme.values.focusColorA,
        dividerColorA: theme.values.dividerColorA,
      });
    }
  }
</script>

<View>
  <ViewContent>
    {#if params.cardId === $view.cards[0].id}
      <Card cardId={$view.cards[0].id}>
        <CardHeader />
        <CardContent>
          <ListHeader title="General" />
          <SelectRow
            label="Theme"
            value={$settings.themeId}
            options={[
              { id: 'light', label: 'Light' },
              { id: 'dim', label: 'Dim' },
              { id: 'dark', label: 'Dark' },
            ]}
            onChange={(val) => handleChange('themeId', val)}
          />
          <ColorPickerRow
            label="Accent Color"
            value={{
              h: $settings.accentColorH,
              s: $settings.accentColorS,
              l: $settings.accentColorL,
            }}
            onChange={(val) =>
              settings.update({
                accentColorH: val.h,
                accentColorS: val.s,
                accentColorL: val.l,
              })}
          />
          <SelectRow
            label="Display Density"
            value={$settings.displayDensity}
            options={[
              { id: Density.Compact, label: 'Compact' },
              { id: Density.Normal, label: 'Normal' },
              { id: Density.Spacious, label: 'Spacious' },
            ]}
            onChange={(val) => handleChange('displayDensity', val)}
          />
          <ListHeader title="Cards" />
          <ColorPickerRow
            label="Background Color"
            value={{
              h: $settings.cardColorH,
              s: $settings.cardColorS,
              l: $settings.cardColorL,
            }}
            onChange={(val) =>
              settings.update({
                cardColorH: val.h,
                cardColorS: val.s,
                cardColorL: val.l,
              })}
          />
          <NumericRangeRow
            label="Border Radius"
            value={$settings.borderRadius}
            valueLabel="px"
            min={0}
            max={32}
            onChange={(val) => handleChange('borderRadius', val)}
          />
          <NumericRangeRow
            label="Focus Strength"
            value={$settings.focusColorA}
            valueLabel="%"
            min={0}
            max={100}
            onChange={(val) => handleChange('focusColorA', val)}
          />
          <NumericRangeRow
            label="Divider Strength"
            value={$settings.dividerColorA}
            valueLabel="%"
            min={0}
            max={100}
            onChange={(val) => handleChange('dividerColorA', val)}
          />
          <ListHeader title="Text" />
          <ColorPickerRow
            label="Text Color"
            value={{
              h: $settings.textColorH,
              s: $settings.textColorS,
              l: $settings.textColorL,
            }}
            onChange={(val) =>
              settings.update({
                textColorH: val.h,
                textColorS: val.s,
                textColorL: val.l,
              })}
          />
          <SelectRow
            label="Text Size"
            value={$settings.textSize}
            options={[
              { id: TextSize.Smallest, label: 'Smallest' },
              { id: TextSize.Small, label: 'Small' },
              { id: TextSize.Medium, label: 'Medium' },
              { id: TextSize.Large, label: 'Large' },
              { id: TextSize.Largest, label: 'Largest' },
            ]}
            onChange={(val) => handleChange('textSize', val)}
          />
          <SelectRow
            label="Text Weight"
            value={$settings.textWeight}
            options={[
              { id: TextWeight.Light, label: 'Light' },
              { id: TextWeight.Medium, label: 'Medium' },
              { id: TextWeight.Heavy, label: 'Heavy' },
            ]}
            onChange={(val) => handleChange('textWeight', val)}
          />
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[1].id}
      <Card cardId={$view.cards[1].id}>
        <CardHeader />
        <CardContent>
          <ListHeader title="General" />
          <SelectRow
            label="Animation Speed"
            value={$settings.animationSpeed}
            options={[
              { id: Animations.Instant, label: 'Instant' },
              { id: Animations.Fast, label: 'Fast' },
              { id: Animations.Normal, label: 'Normal' },
              { id: Animations.Slow, label: 'Slow' },
            ]}
            onChange={(val) => handleChange('animationSpeed', val)}
          />
          <ListHeader title="Shortcut Keys" />
          <ToggleRow
            label="Enable"
            value={$settings.enableShortcutKeys}
            onChange={(val) => handleChange('enableShortcutKeys', val)}
          />
          <SelectRow
            label="Position"
            value={$settings.shortcutKeyLocation}
            options={[
              { id: 'left', label: 'Left' },
              { id: 'right', label: 'Right' },
              { id: 'hidden', label: 'Hidden' },
            ]}
            onChange={(val) => handleChange('shortcutKeyLocation', val)}
          />
          <SelectRow
            label="Color"
            value={$settings.shortcutKeyColor}
            options={[
              { id: 'primary', label: 'Primary' },
              { id: 'secondary', label: 'Secondary' },
              { id: 'accent', label: 'Accent' },
            ]}
            onChange={(val) => handleChange('shortcutKeyColor', val)}
          />
        </CardContent>
      </Card>
    {:else if params.cardId === $view.cards[2].id}
      <Card cardId={$view.cards[2].id}>
        <CardHeader />
        <CardContent>
          <ToggleRow
            label="Show Help Text"
            value={$settings.showHelpText}
            onChange={(val) => handleChange('showHelpText', val)}
          />
        </CardContent>
      </Card>
    {/if}
  </ViewContent>
</View>
