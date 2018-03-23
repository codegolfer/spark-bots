<template>
  <div class="panel panel-primary">

    <div class="panel-heading apt-addheading"
      @click="hidepanel=!hidepanel">
      <span class="glyphicon glyphicon-plus"></span> Add Spark Bot
    </div><!-- panel-heading -->

    <div class="panel-body"
      :class="{ hide: hidepanel }">

      <form class="add-appointment form-horizontal"
        @submit.prevent="requestAdd">

        <div class="form-group">
          <label class="col-sm-2 control-label" htmlFor="petName">Bot Name</label>
          <div class="col-sm-10">
            <input type="text" class="form-control" id="petName" placeholder="Bot's Name" 
            v-model="formData.petName" />
          </div><!-- col-sm-10 --> 
        </div><!-- form-group --> 

        <div class="form-group">
          <label class="col-sm-2 control-label" htmlFor="petOwner">Bot Email</label>
          <div class="col-sm-10">
            <input type="text" class="form-control"
              id="petOwner" placeholder="Bot's Email" 
              v-model="formData.petOwner" />
          </div><!-- col-sm-10 -->
        </div><!-- form-group --> 

        <div class="form-group">
          <label class="col-sm-2 control-label" htmlFor="aptDate">Date Created</label>
          <div class="col-sm-4">
            <input type="date" class="form-control" id="aptDate" 
            v-model="formData.aptDate" />
          </div><!-- col-sm-4 --> 
          <label class="col-sm-2 control-label" htmlFor="aptTime">Time</label>
          <div class="col-sm-4">
            <input type="time" class="form-control" id="aptTime" 
            v-model="formData.aptTime" />
          </div><!-- col-sm-4 --> 
        </div><!-- form-group -->

        <div class="form-group">
          <label class="col-sm-2 control-label" htmlFor="aptNotes">Bot Details</label>
          <div class="col-sm-10">
            <textarea class="form-control" rows="4" cols="50" id="aptNotes" placeholder="Bot's Details" 
            v-model="formData.aptNotes"></textarea>
          </div><!-- col-sm-10 --> 
        </div><!-- form-group -->

        <div class="form-group">
          <div class="col-sm-offset-2 col-sm-10">
            <button type="submit" class="btn btn-primary pull-right">Add Bot</button>
          </div><!-- col-sm-offset-2 --> 
        </div><!-- form-group -->

      </form>
    </div><!-- panel-body -->
  </div><!-- panel-primary -->
</template>

<script>

export default {

  name: 'AddAppointments',
  data() {
    return {
      hidepanel: true,
      formData: []
    } //return
  }, //data
  methods: {
    requestAdd: function() {
      var parsedData = {
        petName: this.formData.petName,
        petOwner: this.formData.petOwner,
        aptDate: this.formData.aptDate + ' ' + this.formData.aptTime,
        aptNotes: this.formData.aptNotes
      }
      this.$emit('addRecord', parsedData);
      this.formData = [];
      this.hidepanel = true;
    } //requestAdd
  } //methods
} //default
</script>

<style scoped>

  .panel-heading {
    cursor: pointer;
  }

</style>
 