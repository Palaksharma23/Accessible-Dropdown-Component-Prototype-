<template>
  <div class="dropdown">
    <button
      href="#"
      class="dropbtn"
      @click="toggleVisibility"
      v-on:keydown.space.exact.prevent="toggleVisibility"
      v-on:keydown.esc.exact="hideDropdown"
      v-on:keydown.shift.tab="hideDropdown"
      v-on:keydown.up.exact.prevent="startArrowKeys"
      v-on:keydown.down.exact.prevent="startArrowKeys"
    >
      Dropdown
    </button>
    <div v-if="isVisible" ref="dropdown" class="dropdown-content">
      <a
        href="/1"
        v-on:keydown.down.exact.prevent="focusNext(true)"
        v-on:keydown.up="focusPrevious(true)"
        v-on:keydown.esc.exact="hideDropdown"
        v-on:keydown.enter.exact="click"
        @click="click"
      >
        Option 1 
      </a>

      <a
        href="/2"
        v-on:keydown.up="focusPrevious(true)"
        v-on:keydown.down.exact.prevent="focusNext(true)"
        v-on:keydown.enter.exact="click"
        @click="click"
      >
        Option 2
      </a>

      <a
        href="/3"
        v-on:keydown.up="focusPrevious(true)"
        v-on:keydown.down.exact.prevent="focusNext(true)"
        v-on:keydown.esc.exact="hideDropdown"
        v-on:keydown.enter.exact="click"
        @click="click"
      >
        Option 3
      </a>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isVisible: false,
      focusedIndex: 0,
    };
  },
  methods: {
    toggleVisibility() {
      this.isVisible = !this.isVisible;
    },
    hideDropdown() {
      this.isVisible = false;
      this.focusedIndex = 0;
    },
    startArrowKeys() {
      if (this.isVisible) {
        // this.$refs.account.focus()
        const startkey = this.$refs.dropdown.children[0];
        // console.log(editButtonRef);
        // editButtonRef.style.backgroundColor = '#66bb6a';
        startkey.focus();
      }
    },
    focusPrevious(isArrowKey) {
      if (this.focusedIndex == 0) {
        this.focusedIndex = 2;
      } else {
        this.focusedIndex = this.focusedIndex - 1;
      }
      // console.log(this.focusedIndex);
      if (isArrowKey) {
        this.focusItem();
      }
    },
    focusNext(isArrowKey) {
      if (this.focusedIndex == 2) {
        this.focusedIndex = 0;
      } else {
        this.focusedIndex = this.focusedIndex + 1;
      }
      // console.log(this.focusedIndex);

      if (isArrowKey) {
        this.focusItem();
      }
    },
    focusItem() {
      const focuseditem = this.$refs.dropdown.children[this.focusedIndex];
      // here.style.backgroundColor = '#66bb6a'
      // console.log(here.href);
      focuseditem.focus();
    },
    click() {
      window.open(this.$refs.dropdown.children[this.focusedIndex].href,"_self")
    },
  },
};
</script>

<style>
/* Style The Dropdown Button */
.dropbtn {
  background-color: #d0afff;
  color: white;
  padding: 16px;
  font-size: 16px;
  border: none;
  cursor: pointer;
}

/* The container <div> - needed to position the dropdown content */
.dropdown {
  background-color: #d0afff;
  position: relative;
  display: inline-block;
}

/* Dropdown Content (Hidden by Default) */
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px #d0afff;
  z-index: 1;
}

/* Links inside the dropdown */
a {
  color: 	black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
  background-color: #d0afff;
}

a:focus {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
  background-color: #ffa32d;
}

/* Change color of dropdown links on hover */
a:hover {
  background-color: white;
}

/* Show the dropdown menu on hover */
.dropdown:hover .dropdown-content {
  display: block;
}

/* Change the background color of the dropdown button when the dropdown content is shown */
.dropdown:hover .dropbtn {
  background-color: #ffa32d;
}
</style>
