<template>
    <div class="container">
        <div :class="{'search-box--open': isOpen}"
             class="search-box">
            <input ref="searchInput"
                   v-model="searchText"
                   class="search-box__input"
                   name="search"
                   placeholder="Search......"
                   required
                   type="search"
                   @search="keyUpHandler"
                   @keyup="keyUpHandler" />
            <span v-if="!showIcon"
                  class="search-box__submit"
                  @click="doSearch">
                <span class="material-icons">search</span>
            </span>
            <span v-if="showIcon"
                  class="search-box__icon"
                  @click="submitIconClicked">
                <span class="material-icons">search</span>
            </span>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'expanding-search-box',

        data() {
            return {
                isOpen: false,
                searchText: '',
                showIcon: true,
            }
        },

        methods: {
            /**
             * Handles the click event on the search icon.
             * Opens and closes the search box.
             */
            submitIconClicked() {
                const searchInput = this.$refs.searchInput
                if (!this.isOpen) {
                    this.isOpen = true
                    searchInput.focus()
                } else {
                    this.isOpen = false
                }
            },

            /**
             * Handles the key up event on the search box.
             * If there is any text in the box, then display the submit button.
             * Else display the search icon.
             */
            keyUpHandler() {
                if (this.searchText.trim().length > 0) {
                    this.showIcon = false
                } else {
                    this.showIcon = true
                    this.searchText = ''
                }
            },

            /**
             * Handles the click event on the submit icon and does the search
             */
            doSearch() {
                if (this.searchText.trim().length > 0) {
                    alert(`Search for "${ this.searchText.trim() }"`)
                } else {
                    this.keyUpHandler()
                }
            },
        },
    }
</script>

<style scoped>
  .container {
    width: 600px;
    margin: 50px auto;
  }

  .search-box {
    position: relative;
    min-width: 50px;
    width: 0;
    height: 50px;
    float: right;
    overflow: hidden;
    transition: width 0.3s;
  }

  .search-box__input {
    top: 0;
    right: 0;
    border: 0;
    outline: 0;
    background: #dcddd8;
    width: 100%;
    height: 50px;
    margin: 0;
    padding: 0 55px 0 20px;
    font-size: 20px;
    color: red;
  }
  
  .search-box__icon,
  .search-box__submit {
    width: 50px;
    height: 50px;
    display: block;
    position: absolute;
    top: 0;
    font-size: 22px;
    right: 0;
    padding: 0;
    margin: 0;
    border: 0;
    outline: 0;
    line-height: 50px;
    text-align: center;
    cursor: pointer;
    color: #FFFFFF;
    background: #ff0000;
  }
  
  .search-box__submit {
    background-color: purple;
  }


  .search-box__icon span,
  .search-box__submit span {
    font-size: 32px;
    padding-top: 8px;
  }

  .search-box--open {
    width: 100%;
  }

  .show {
    display: block;
  }

  .hide {
    display: none;
  }

</style>
