<script lang="ts">
	import { Button, Modal, type ModalProps } from "flowbite-svelte";
	import { type Snippet } from 'svelte';

    interface Props {
        triggerText?: string;
        titleText?: string;
        cancelText?: string;
        confirmText?: string;
        defaultOpen?: boolean;
        onConfirm: Function;
        children: Snippet;
    }

    let {
        triggerText = "",
        titleText = "",
        cancelText = "Cancel",
        confirmText = "Save",
        defaultOpen = false,
        onConfirm,
        children
    }: Props = $props();

    let open = $state(defaultOpen);
    
    const onaction: ModalProps["onaction"] = ({ action }) => {
        if (action === "confirm") {
            onConfirm();
        }
    }

</script>

{#if triggerText}
    <Button onclick={() => (open = true)}>{triggerText}</Button>
{/if}

<Modal 
    title={titleText} 
    form bind:open={open}
    {onaction}
>
  {@render children()}
  {#snippet footer()}
    <footer class="flex justify-center gap-2 w-full">
        <Button type="submit" value="confirm">{confirmText}</Button>
        <Button type="submit" value="cancel" color="alternative">{cancelText}</Button>
    </footer>
  {/snippet}
</Modal>
