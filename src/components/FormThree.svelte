<script>
    import { FormThree, CurrentForm } from "../store.js";
    let organizationName = "";
    let organizationNumber = "";
    let address = "";
    let numberOfUsers = "";
    let error = {};
    const handleSubmit = () => {
       
      FormThree.setValues(organizationName,organizationNumber,address,numberOfUsers);
      CurrentForm.formopenfour();
    };
  </script>
  
  <style>
    .container {
      width: 30%;
      height: 60%;
      background-color: #d0d0d04a;
      border-radius: 10px;
      padding: 10px;
      box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.5);
    }
  
    .container h1 {
      text-align: center;
      margin-bottom: 10px;
      font-size: 40px;
      font-weight: bold;
    }
  
    .container hr {
      width: 100%;
      margin: 0 auto;
      margin-bottom: 10px;
    }
  
    .form div {
      display: flex;
      flex-direction: column;
      margin-bottom: 20px;
    }
  
    .form div label {
      text-align: center;
      font-size: 20px;
      font-weight: bold;
      margin-bottom: 5px;
    }
  
    .form div input {
      padding: 10px;
      border-radius: 10px;
      outline: none;
      font-size: 20px;
      width: 70%;
      margin: 0 auto;
      transform: all 0.4s ease-in;
    }
  
    .form div input:active,
    .form div input:focus {
      width: 96%;
    }
  
    .form div code {
      color: red;
      text-align: center;
      margin-top: 10px;
    }
  
    .form div button {
      width: 70%;
      margin: 0 auto;
      margin-top: 20px;
      padding: 10px 10px;
      font-size: 20px;
      outline: none;
      background-color: #fff;
      border-radius: 10px;
      transition: all 0.4s ease-out;
    }
  
    .form div button:hover {
      transform: translateY(-1px);
      box-shadow: 2px 2px 2px rgba(0, 0, 0, 0.7);
    }
  
    .form div button:active {
      transform: translateY(1px);
    }
  </style>
  
  <div class="container">
    <h1>Form Three</h1>
    <hr />
    <form class="form" on:submit|preventDefault={handleSubmit}>
      <div>
        <label>Organization Name</label>
        <input
          type="text"
          placeholder="Organization Name"
          bind:value={organizationName} />
        {#if error.organizationName}
          <code>{error.organizationName}</code>
        {/if}
      </div>
      <div>
        <label>Organization Number</label>
        <input
          type="text"
          placeholder="Organization Number"
          bind:value={organizationNumber}/>
        {#if error.organizationNumber}
          <code>{error.organizationNumber}</code>
        {/if}
      </div>
      <div>
        <label>Address</label>
        <input
          type="text"
          placeholder="Address"
          bind:value={address}/>
        {#if error.address}
          <code>{error.address}</code>
        {/if}
      </div>
      <div>
        <label>Number Of Users</label>
        <input
          type="text"
          placeholder="Number Of Users"
          bind:value={numberOfUsers}/>
        {#if error.numberOfUsers}
          <code>{error.numberOfUsers}</code>
        {/if}
      </div>
      <div>
        <button type="submit">Next</button>
      </div>
    </form>
  </div>
  