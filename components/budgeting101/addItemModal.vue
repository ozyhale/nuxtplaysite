<template>
  <div>
    <div class="modal-card" style="width: auto">
      <header class="modal-card-head">
        Add Item
      </header>
      <section class="modal-card-body">
        <b-field horizontal label="Name">
            <b-input></b-input>
        </b-field>
        <b-field horizontal label="Cost">
            <b-input type="number" value="0"></b-input>
        </b-field>
      </section>
      <footer class="modal-card-foot">
        <button class="button" type="button" @click="$parent.close()">Close</button>
        <button class="button is-primary">Save</button>
      </footer>
    </div>
  </div>
</template>