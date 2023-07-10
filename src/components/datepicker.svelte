<script lang="ts">
    import { onMount } from 'svelte';
    import flatpickr from 'flatpickr';
	import { Input } from 'flowbite-svelte';

    let selectedTime: Date | null = null;
    let inputElement: HTMLInputElement | null = null;

    onMount(() => {
      if (inputElement) {
        flatpickr(inputElement, {
          enableTime: true,
          noCalendar: true,
          dateFormat: 'H:i',
          onChange: (selectedTimes: Date[]) => {
            selectedTime = selectedTimes[0];
          }
        });
      }
    });
  </script>

  <div>
    <Input type="text" bind:value={selectedTime} placeholder="Select a time" class="px-4 py-2 bg-white border border-gray-300 rounded shadow-sm focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent" />
  </div>
