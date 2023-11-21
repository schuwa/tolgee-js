<script lang="ts">
    import type { NsType, TranslationKey } from '@tolgee/web';
  import getTranslateInternal from './getTranslateInternal';

  type Props = {
    keyName: string;
    params?: Record<string, unknown>;
    noWrap?: boolean;
    defaultValue?: string;
    ns?: NsType;
    language?: string;
  };

  let {
    keyName,
    params,
    noWrap,
    defaultValue,
    ns,
    language,
  } = $props<Props>();

  if (!keyName) {
    console.error('Missing keyName prop!');
  }

  const { t } = getTranslateInternal();
</script>

{$t({
  key: keyName,
  params: params,
  noWrap: noWrap,
  defaultValue: defaultValue,
  ns,
  language,
})}
