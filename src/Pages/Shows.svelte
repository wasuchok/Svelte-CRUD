
<script>
    import { onMount } from 'svelte';
    import axios from 'axios'
  
    let users = []
  
    async function getData() {
      await axios.get('https://www.melivecode.com/api/users')
      .then(res => {
        if(res.status == 200) {
          users = res.data
        }
      })
    }

    async function deleteUser(id) {
      await axios.delete('https://www.melivecode.com/api/users/delete', {
        data : {
          id
        }
      }).then((response) => {
        getData()
        console.log(response)
      })
    }
  
    onMount(() => {
      getData()
    })
  
  
  </script>

  <a href='/#/add' class="btn btn-success">เพิ่มข้อมูลผู้ใช้</a>
  <table class="table table-hover">
    <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">รูป</th>
        <th scope="col">ชื่อจริง</th>
        <th scope="col">นามสกุล</th>
        <th scope="col">ชื่อผู้ใช้</th>
        <th scope="col">เครื่องมือ</th>
      </tr>
    </thead>
    <tbody>
      {#each users as user}
      <tr>
        <th scope="row">{user.id}</th>
        <td><img src={user.avatar} alt="" class="avatar"></td>
        <td>{user.fname}</td>
        <td>{user.lname}</td>
        <td>{user.username}</td>
        <td>
          <a class="btn btn-primary" href={`/#/edit/${user.id}`}>แก้ไขข้อมูล</a>
          <button class="btn btn-danger" on:click={() => deleteUser(user.id)}>ลบข้อมูล</button>
        </td>
      </tr>
      {/each}
    </tbody>
   
  </table>


<style>
  .avatar {
    width: 50px;
  }
</style>
