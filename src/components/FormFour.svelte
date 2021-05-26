<script>
    import { FormFour, CurrentForm } from "../store.js";
    let cardNumber = "";
    let expirationDate = "";
    let cvv = "";
    let error = {};
    const handleSubmit = () => {
      if (cardNumber.trim() === "") {
        error.cardNumber = "Card Number field is required";
        return;
      }
   
      if (expirationDate.trim() === "") {
        error.expirationDate = "Expiration Date field is required";
        return;
      }
      if (cvv.trim() === "") {
        error.cvv = "CVV field is required";
        return;
      }
     
      FormFour.setValues(cardNumber,expirationDate,cvv);
      CurrentForm.success();
    };
  </script>
  
  <style>
    .container {
      width: 30%;
      height: 50%;
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
    <h1>Form Four</h1>
    <hr />
    <form class="form" on:submit|preventDefault={handleSubmit}>
      <div>
        <label>Card Number</label>
        <input
          type="text"
          placeholder="Card Number"
          bind:value={cardNumber} />
        {#if error.cardNumber}
          <code>{error.cardNumber}</code>
        {/if}
      </div>      
      <div>
        <label>Expiration Date</label>
        <input
          type="date"
          placeholder="Expiration Date"
          bind:value={expirationDate}/>
        {#if error.expirationDate}
          <code>{error.expirationDate}</code>
        {/if}
      </div>
      <div>
        <label>CVV</label>
        <input
          type="text"
          placeholder="CVV"
          bind:value={cvv}/>
        {#if error.cvv}
          <code>{error.cvv}</code>
        {/if}
      </div>
      <div>
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
  