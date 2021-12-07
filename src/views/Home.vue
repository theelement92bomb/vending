<template>
  <center>
    <div class="container-fluid">
      <h1>Vending Machine</h1>
      <div>{{ errorMsg }}</div>
      <div class="row">
        <div class="col-lg-2">
          <h1>Admin Mode</h1>
          <label for="password">Admin Password</label>
          <input type="password" v-model="password"><br>
          <button class = "admin" @click="checkPassword()" v-if="adminAllowed == false">Submit</button>
          <button class = "admin" v-if="adminAllowed == true" disabled>Submit</button><br>
          <button v-if="adminAllowed == false" disabled>Admin Mode Off</button>
          <button v-if="adminAllowed == true & adminEnabled == false" @click="switchMode()">Admin Mode Off</button>
          <button v-if="adminAllowed == true & adminEnabled == true" @click="switchMode()" >Admin Mode On</button>
        </div>
        <div class="col-lg-7">
          <div class="row">
            <div class="col-lg-2">
              <button @click="buy(60)">
                Sprite<br />${{ Number(price[0][0]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(61)">
                Coca-Cola<br />${{ Number(price[0][1]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(62)">
                Fanta<br />${{ Number(price[0][2]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(63)">
                Mtn. Dew<br />${{ Number(price[0][3]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(64)">
                Pepsi<br />${{ Number(price[0][4]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(65)">
                7-Up<br />${{ Number(price[0][5]) }}
              </button>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-2">
              <button @click="buy(10)">
                Poland Springs<br />${{ Number(price[1][0]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(11)">
                Aquafina<br />${{ Number(price[1][1]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(12)">
                Costco Water<br />${{ Number(price[1][2]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(13)">
                Evian<br />${{ Number(price[1][3]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(14)">
                Dasani<br />${{ Number(price[1][4]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(15)">
                "Smart"Water<br />${{ Number(price[1][5]) }}
              </button>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-2">
              <button @click="buy(20)">
                Heavy Water<br />${{ Number(price[2][0]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(21)">
                Coffee<br />${{ Number(price[2][1]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(22)">
                Espresso<br />${{ Number(price[2][2]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(23)">
                Dunkin Coffee<br />${{ Number(price[2][3]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(24)">
                Starbucks Espresso<br />${{ Number(price[2][4]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(25)">
                Starbucks Coffee<br />${{ Number(price[2][5]) }}
              </button>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-2">
              <button @click="buy(30)">
                Szechaun Sauce<br />${{ Number(price[3][0]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(31)">
                Ikea Meatball Gravy<br />${{ Number(price[3][1]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(32)">
                Holy Water<br />${{ Number(price[3][2]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(33)">
                Unholy Water<br />${{ Number(price[3][3]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(34)">
                Devil Water<br />${{ Number(price[3][4]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(35)">
                Belle Delphine Bathwater<br />${{ Number(price[3][5]) }}
              </button>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-2">
              <button @click="buy(40)">
                Concentrated Mana<br />${{ Number(price[4][0]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(41)">
                Blessed Waters<br />${{ Number(price[4][1]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(42)">
                Tear of the Goddess<br />${{ Number(price[4][2]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(43)">
                Blood of Christ<br />${{ Number(price[4][3]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(44)">
                Coaxium<br />${{ Number(price[4][4]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(45)">
                Liquid Tibanna<br />${{ Number(price[4][5]) }}
              </button>
            </div>
          </div>
          <div class="row">
            <div class="col-lg-2">
              <button @click="buy(50)">
                Pan-Galactic Gargleblaster<br />${{ Number(price[5][0]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(51)">
                Liquid Metal<br />${{ Number(price[5][1]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(52)">
                Mimetic Polyalloy<br />${{ Number(price[5][2]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(53)">
                Spice Melange<br />${{ Number(price[5][3]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(54)">
                Deuterium<br />${{ Number(price[5][4]) }}
              </button>
            </div>
            <div class="col-lg-2">
              <button @click="buy(55)">
                Antimatter<br />${{ Number(price[5][5]) }}
              </button>
            </div>
          </div>
        </div>
        <div class="col-lg-3">
          <h1>Insert Money Here</h1>
          Inserted Money: ${{ balance }} <br />
          Your Change: ${{ change }} <br />
          <button @click="addBal(0.01)">Penny</button>
          <button @click="addBal(0.05)">Nickle</button>
          <button @click="addBal(0.1)">Dime</button><br />
          <button @click="addBal(0.25)">Quarter</button>
          <button @click="addBal(1)">1 Dollar</button>
          <button @click="addBal(5)">5 Dollars</button><br />
          <button @click="addBal(10)">10 Dollars</button>
          <button @click="addBal(20)">20 Dollars</button>
          <button @click="addBal(50)">50 Dollars</button><br />
          <button @click="addBal(100)">100 Dollars</button>
        </div>
      </div>
    </div>
  </center>
</template>

<script>
export default {
  data() {
    return {
      value: "",
      row: "",
      column: "",
      balance: 0,
      change: "",
      errorMsg: "_",
      password:"",
      setPassword:"",
      adminEnabled:false,
      adminAllowed:false,
      stock: [
        [1, 2, 3, 4, 5, 6],
        [9, 2, 4, 2, 1, 9],
        [5, 1, 9, 10, 1, 3],
        [1, 5, 6, 4, 5, 1],
        [3, 4, 9, 4, 10, 0],
        [1, 8, 0, 10, 3, 8],
      ],
      price: [
        [1.75, 1.75, 1.75, 1.75, 1.75, 1.75],
        [1.0, 1.75, 0.25, 1.5, 2.0, 5.0],
        [2.0, 1.5, 1.75, 1.75, 2.25, 2.75],
        [20.0, 12.5, 15.0, 25.0, 27.75, 30.0],
        [50, 55, 60, 65, 70, 70],
        [75, 80, 85, 90, 95, 100],
      ],
    };
  },
  methods: {
    buy(value) {
      this.errorMsg = "_";
      value = String(value);
      this.row = value[0];
      this.column = value[1];
      if(this.row == 6){
        this.row = 0
      }
      if(this.adminEnabled == true){
        this.stock[this.row][this.column] += 1
        return
      }
      if (this.stock[this.row][this.column] > 0) {
        if (this.balance >= this.price[this.row][this.column]){
          this.stock[this.row][this.column] -= 1
          this.change = this.balance - this.price
          this.balance = 0
          this.errorMsg = "Thank you for your purchase";
        }
        else{
          this.errorMsg = "Sorry, you have inadequate funds to purchase this item"
        }
      } else {
        this.errorMsg = "Sorry, this product is out of stock";
      }
    },
    addBal(value) {
      this.balance += value;
      this.errorMsg = "_"
    },
    switchMode(){
      document.getElementById("adminButton");

      if(this.adminEnabled == false){
        this.adminEnabled = true
        this.errorMsg = "Admin Mode Enabled. Click on a product to increase its stock by 1."
      }
      else{
        this.adminEnabled=false
        this.errorMsg = "Admin Mode Disabled"
      }
    },
    checkPassword(){
      if(this.password == this.setPassword){
        this.adminAllowed = true
        this.errorMsg = "Welcome Admin"
      }
      else{
        this.errorMsg = "The Admin Password is Incorrect"
      }
    }
  },
};
</script>

<style scoped>
button {
  width: 100px;
  height: 100px;
}
.admin{
  width: 70px;
  height: 30px;
}
</style>
