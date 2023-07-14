<h1>แก้ไขข้อมูล</h1>

    <div class="mb-3">
      <label for="" class="form-label">ชื่อจริง</label>
      <input type="text" class="form-control" bind:value={user.fname}>
    </div>

    <div class="mb-3">
        <label for="" class="form-label">นามสกุล</label>
        <input type="text" class="form-control" bind:value={user.lname}>
    </div>

    <div class="mb-3">
        <label for="" class="form-label">ชื่อผู้ใช้</label>
        <input type="text" class="form-control" bind:value={user.username}>
      </div>

      <div class="mb-3">
        <label for="" class="form-label">รูป</label>
        <input type="text" class="form-control" bind:value={user.avatar}>
      </div>

    <button type="submit" class="btn btn-primary" on:click={editUser}>Submit</button>
  

  <script>
  import axios from "axios";
  import { onMount } from "svelte";
  import { push } from "svelte-spa-router";
  export let params


    let user = {
        fname : "",
        lname : "",
        username : "",
        avatar : "",
    }

    async function getData() {
        await axios.get(`https://www.melivecode.com/api/users/${params.id}`)
        .then((response) => {
            if(response.status == 200) {
                user = response.data.user
            }
        })
    }

    async function editUser() {
        await axios.put(`https://www.melivecode.com/api/users/update`, {
            id : params.id,
            ...user
        }).then((response) => {
            push('/')
        })
    }

    onMount(getData)

  </script>