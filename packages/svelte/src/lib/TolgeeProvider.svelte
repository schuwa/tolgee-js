<script lang="ts">
  import {setContext} from 'svelte';
  import type {TolgeeInstance} from '@tolgee/web';
  import type {TolgeeSvelteContext} from './types';

  type Props = {
    tolgee: TolgeeInstance;
  };

  let {tolgee} = $props<Props>();

  let isLoading = $state(!tolgee.isLoaded());

  setContext('tolgeeContext', {
    tolgee,
  } as TolgeeSvelteContext);

  $effect(() => {
    tolgee.run().finally(() => {
      isLoading = false
    })

    return () => {
      tolgee.stop();
    };
  });
</script>

<slot/>