<template>
    <div class="note">
      <a href="#" class="note__delete">
        <span class="note__delete-icon"
              @click="deleteNoteItem(note.id)"
        >&times;</span>
      </a>
      <div class="note__content">
        <a href="#" class="note__title"
           @click="openNote(note)"
        >
          <span            v-if="note.title">
            {{ note.title }}
          </span>
          <span v-else>
            Untitled note
          </span>
        </a>
        <p class="note__body"
           v-if="note.body"
        >
          {{ note.body }}
        </p>
        <p v-else>
         <em> Empty </em>
        </p>
      </div>
    </div>
</template>

<script>
import { mapActions } from 'vuex';

export default {
  name: 'noteTemplate',
  props: {
    note: {
      type: Object,
      default: () => {},
    },
  },
  methods: {
    ...mapActions(['openNote', 'deleteNote']),
    deleteNoteItem(id) {
      this.deleteNote(id);
    },
  },
};
</script>

<style scoped lang="scss">
  .note {
    display: flex;
    color: inherit;
    text-decoration: none;
    border-bottom: 2px solid #eee;
    max-width: 100%;
    opacity: .3;
    transition: all .3s ease-in;
    cursor: pointer;

    &:hover {
      opacity: 1;

      .note__delete {
        margin-left: 0;
      }
    }
    &__content {
      padding: 30px;
      flex: 2;
      overflow: hidden;
    }

    &__title {
      display: block;
      font-size: 1em;
      margin: 0;
      font-weight: bold;
      text-decoration: none;
      color: inherit;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    &__body {
      font-size: .9em;
      margin: 0;
      font-weight: 500;
      text-decoration: none;
      color: inherit;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    &__delete {
      position: relative;
      margin-left: -50px;
      width: 50px;
      display: block;
      background: #cc4466;
      min-height: 100%;
      color: #fff;

      &-icon {
        position: absolute;
        left: 50%;
        top: 50%;
        font-size: 1.5em;
        font-weight: bold;
        transform: translate(-50%,-50%);
      }
    }
  }
</style>
