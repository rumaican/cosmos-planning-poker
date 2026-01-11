<script lang="ts">
  import { AppConfig } from '../../config';

  interface Props {
    class?: string;
  }

  let { class: klass = '' }: Props = $props();
  const { PathPrefix } = AppConfig;
</script>

<img src="{PathPrefix}/img/cosmos_logo.png" alt="Team Cosmos" class={klass} />
