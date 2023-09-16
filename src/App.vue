<script setup>
import { ref } from 'vue'

const booking = [];

const buttonText = ref('จอง');
const buttonText2 = ref('จอง');
const buttonText3 = ref('จอง');
const buttonText4 = ref('จอง'); // Initial button text
let isBooked = false; // Initial booking state
let isBooked2 = false;
let isBooked3 = false;
let isBooked4 = false;
const toggleButton = () => {
  if (isBooked) {
    buttonText.value = 'จอง'; // Change text to "จอง" when canceled
  } else {
    buttonText.value = 'ยกเลิก'; // Change text to "ยกเลิก" when booked
  }
  isBooked = !isBooked; // Toggle the booking state
  this.booking.push("res1");
};

const toggleButton2 = () => {
  if (isBooked2) {
    buttonText2.value = 'จอง'; // Change text to "จอง" when canceled
  } else {
    buttonText2.value = 'ยกเลิก'; // Change text to "ยกเลิก" when booked
  }
  isBooked2 = !isBooked2; // Toggle the booking state
  this.booking.push("res2");
};

const toggleButton3 = () => {
  if (isBooked3) {
    buttonText3.value = 'จอง'; // Change text to "จอง" when canceled
  } else {
    buttonText3.value = 'ยกเลิก'; // Change text to "ยกเลิก" when booked3
  }
  isBooked3 = !isBooked3; // Toggle the booking state
  this.booking.push("res3")
};

const toggleButton4 = () => {
  if (isBooked4) {
    buttonText4.value = 'จอง'; // Change text to "จอง" when canceled
  } else {
    buttonText4.value = 'ยกเลิก'; // Change text to "ยกเลิก" when booked4
  }
  isBooked4 = !isBooked4; // Toggle the booking state
  this.booking.push("res4")
  
};



</script>

<template>
  <h1>Cafe</h1>
  <div class="card-container">
    <div class="card-grid">
      <!-- Card 1 -->
      <div class="card">
        <img src="https://img.wongnai.com/p/1920x0/2020/02/07/ec1f6f3626fb477a86a0e9a7d3fb61e8.jpg" class="card-img-top" alt="...">
        <div class="card-body">
          <button class="btn" @click="toggleButton">{{ buttonText }}</button>
        </div>
      </div>

      <!-- Card 2 -->
      <div class="card">
        <img src="https://img.wongnai.com/p/1920x0/2023/07/21/8551488ad9644399a90c4740c72e7dfc.jpg" class="card-img-top" alt="...">
        <div class="card-body">
          <button class="btn" @click="toggleButton2">{{ buttonText2 }}</button>
        </div>
      </div>

      <!-- Card 3 -->
      <div class="card">
        <img src="https://img.wongnai.com/p/1920x0/2019/09/15/f0797c2563e34d35b3c23da50c9afb5a.jpg" class="card-img-top" alt="...">
        <div class="card-body">
          <button class="btn" @click="toggleButton3">{{ buttonText3 }}</button>
        </div>
      </div>

      <!-- Card 4 -->
      <div class="card">
        <img src="https://img.wongnai.com/p/1920x0/2020/07/02/fe982ae2c9484ea29c11264f0e347a63.jpg" class="card-img-top" alt="...">
        <div class="card-body">
          <button class="btn" @click="toggleButton4">{{ buttonText4 }}</button>
        </div>
      </div>
    </div>
  </div>

  
    <div id="reservation-form">

      <div>

    <table>
      <tbody>
        <tr v-for="(bookingItem, index) in booking" :key="index">
          <td>{{ bookingItem.name }}</td>
          <!-- Add other table columns here based on your data structure -->
        </tr>
      </tbody>
      </table>
    </div>

      <h2>จองโต๊ะ</h2>
      <form @submit.prevent="submitReservation" class="reservation-form">
        <!-- ข้อมูลการจอง -->
        <div class="form-group">
          <label for="reservationName">ชื่อผู้จอง:</label>
          <input type="text" id="reservationName" v-model="reservationName" required>
        </div>
        <div class="form-group">
          <label for="reservationNumber">เบอร์โทรศัพท์:</label>
          <input type="number" id="reservationNumber" v-model="reservationNumber" required class="same-width">
        </div>
        <div class="form-group">
          <label for="dateTime">วันและเวลา:</label>
          <input
            type="datetime-local"
            id="dateTime"
            v-model="dateTime"
            :min="minDateTime"
            required
          >
        </div>
        <!-- ปุ่มยืนยันการจอง -->
        <button type="submit" class="btn btn-primary btn-reservation">ยืนยันการจอง</button>
      </form>
    </div>
 
</template>

<script>


</script>
<style scoped>

h1 {
    font-size: 32px;
    margin-bottom: 20px;
    color: #007bff; /* สีข้อความหัวข้อ */
    text-align: center;
    background-color: rgb(190, 190, 190);
    padding: 25px;
  }

.card-container {
  display: grid;
  justify-content: center;
  align-items: center;
  margin-top: 20px;
}

.card-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 20px;
  justify-content: center;
}

.card {
  width: 18rem;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.reservation-form {
  background-color: #fff;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  margin-top: 20px;
}

h2 {
  font-size: 24px;
  color: #007bff;
  margin-top: 50px;
  text-align: center;
}

label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
}

input[type="text"],
input[type="datetime-local"],
input[type="number"] {
  width: 100%;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-bottom: 10px;
}

button[type="submit"] {
  background-color: #007bff;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button[type="submit"]:hover {
  background-color: #0056b3;
}

.same-width {
  width: 100%;
}

.btn {
  background-color: #28a745; /* Green background color */
  color: #fff; /* White text color */
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.btn:hover {
  background-color: #dc3545; /* Red background color on hover */
}

</style>