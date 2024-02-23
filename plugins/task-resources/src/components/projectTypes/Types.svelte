<!--
// Copyright © 2020, 2021 Anticrm Platform Contributors.
// Copyright © 2021 Hardcore Engineering Inc.
//
// Licensed under the Eclipse Public License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License. You may
// obtain a copy of the License at https://www.eclipse.org/legal/epl-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
//
// See the License for the specific language governing permissions and
// limitations under the License.
-->
<script lang="ts">
  import { Ref, WithLookup } from '@hcengineering/core'
  import { ProjectType } from '@hcengineering/task'
  import { Icon, Label, IconOpenedArrow } from '@hcengineering/ui'
  import { createEventDispatcher } from 'svelte'

  export let type: ProjectType | undefined
  export let typeId: Ref<ProjectType> | undefined

  export let types: WithLookup<ProjectType>[] = []

  const dispatch = createEventDispatcher()
  function select (item: ProjectType): void {
    typeId = item._id
    dispatch('change', typeId)
  }
</script>

{#each types as typeItem}
  <button
    class="task-trekTaskNavLink-container font-regular-14"
    class:selected={typeItem._id === typeId}
    on:click={() => {
      select(typeItem)
    }}
  >
    <div class="task-trekTaskNavLink-avatar">
      {#if typeItem.$lookup?.descriptor?.icon}
        <div class="task-trekTaskNavLink-icon">
          <Icon icon={typeItem.$lookup?.descriptor?.icon} size={'small'} fill={'currentColor'} />
        </div>
      {/if}
    </div>
    {#if typeItem.$lookup?.descriptor}
      <div class="task-trekTaskNavLink-content">
        <span class="task-trekTaskNavLink-content__title">{typeItem.name}</span>
        <span class="task-trekTaskNavLink-content__descriptor">
          <Label label={typeItem.$lookup?.descriptor.name} />
        </span>
      </div>
    {/if}
    {#if typeItem._id === typeId}
      <div class="task-trekTaskNavLink-icon right">
        <IconOpenedArrow size={'small'} />
      </div>
    {/if}
  </button>
{/each}

<style lang="scss">
  .task-trekTaskNavLink-container {
    display: flex;
    align-items: center;
    flex-shrink: 0;
    gap: 0.75rem;
    padding: 0 0.75rem 0 0.5rem;
    height: 3.5rem;
    min-width: 0;
    border: none;
    border-radius: 0.375rem;
    outline: none;

    &.selected {
      cursor: auto;
    }
    .task-trekTaskNavLink-avatar {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-shrink: 0;
      width: 2.5rem;
      height: 2.5rem;
      min-width: 0;
      background-color: var(--global-ui-BackgroundColor);
      border-radius: 0.375rem;
    }
    .task-trekTaskNavLink-icon {
      flex-shrink: 0;
      width: 1rem;
      height: 1rem;
      color: var(--global-secondary-TextColor);

      &.right {
        visibility: hidden;
      }
    }
    .task-trekTaskNavLink-content {
      display: flex;
      flex-direction: column;
      gap: 0.125rem;
      flex-grow: 1;
      min-width: 0;
      min-height: 0;

      &__title,
      &__descriptor {
        white-space: nowrap;
        word-break: break-all;
        text-overflow: ellipsis;
        overflow: hidden;
        text-align: left;
        min-width: 0;
      }
      &__title {
        color: var(--global-primary-TextColor);
      }
      &__descriptor {
        color: var(--global-secondary-TextColor);
      }
    }

    &:hover {
      background-color: var(--global-ui-hover-highlight-BackgroundColor);
    }
    &.selected {
      background-color: var(--global-ui-highlight-BackgroundColor);

      .task-trekTaskNavLink-icon {
        color: var(--global-accent-TextColor);

        &.right {
          visibility: visible;
        }
      }
      .task-trekTaskNavLink-content .task-trekTaskNavLink-content__title {
        font-weight: 700;
        color: var(--global-accent-TextColor);
      }
      .task-trekTaskNavLink-content .task-trekTaskNavLink-content__descriptor {
        color: var(--global-primary-TextColor);
      }
    }
  }
</style>
