<h1>เพิ่มผู้ใช้</h1>

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
        <label for="" class="form-label">อีเมล</label>
        <input type="email" class="form-control" bind:value={user.email}>
      </div>

      <div class="mb-3">
        <label for="" class="form-label">รูป</label>
        <input type="text" class="form-control" bind:value={user.avatar}>
      </div>

      <div class="mb-3">
        <label for="" class="form-label">รหัสผ่าน</label>
        <input type="password" class="form-control" bind:value={user.password}>
      </div>

      <div class="mb-3">
        <label for="" class="form-label">ยืนยันรหัสผ่าน</label>
        <input type="password" class="form-control" bind:value={user.confirm_password}>
      </div>

    <button type="submit" class="btn btn-primary" on:click={() => submit()}>Submit</button>
  

  <script>
  import axios from "axios";
  import { push } from "svelte-spa-router";

    let user = {
        fname : "",
        lname : "",
        username : "",
        email : "",
        avatar : "",
        password : "",
        confirm_password : ""
    }

    async function submit() {
        if(user.password == user.confirm_password) {
            await axios.post('https://www.melivecode.com/api/users/create', user)
            .then((response) => {
                alert('เพิ่มข้อมูลสำเร็จ')
                push('/')
            })
        } else {
            alert("รหัสผ่านไม่ถูกต้อง")
        }
    }
  </script>