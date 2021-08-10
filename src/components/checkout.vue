<template>
  <div>
    <div class="checkout">
      <v-container class="checkout-container">
        <v-row>
          <div class="checkout-label">Checkout&Review</div>
        </v-row>
        <v-row class>
          <v-col cols="12" class="px-3">
            <v-card class="pa-3">
              <v-row class="tt">
                <v-col class="ml-9" sm="6">product</v-col>
                <v-col class="text-center">price/cycle</v-col>
              </v-row>
              <v-divider></v-divider>
              <v-row class="tt">
                <v-col class="ml-9" sm="6">WifinityTv {{ plan }} package</v-col>
                <v-col class="text-center">$12/ 3 months</v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>Select currency
        <v-card class="select-currency" width="50%">
          <v-select :items="currency" outlined label="select currency"></v-select>
        </v-card>promotion
        <v-card class="promotion">
          <v-text-field class="mt-2" label="Enter Promo code if you have one" outlined></v-text-field>
        </v-card>Billing details
        <v-card class="billing" pa="3">
          <v-row>
            <v-col cols="12" sm="6">
              <v-text-field label="First Name" outlined mx="5"></v-text-field>
            </v-col>
            <v-col cols="12" sm="6">
              <v-text-field label="Last Name" outlined></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="12" sm="6">
              <v-text-field label="Email Address" outlined></v-text-field>
            </v-col>
            <v-col cols="12" sm="6">
              <v-text-field label="Mobile Number" outlined></v-text-field>
            </v-col>
          </v-row>
        </v-card>
        <v-row class="d-flex justify-center">
          <form>
            <v-btn @click="payNow">Checkout</v-btn>
          </form>
        </v-row>
        <div>
          <div v-if="!paidFor"></div>
          <div v-if="paidFor"></div>
          <div ref="paypal"></div>
        </div>
      </v-container>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      plan: this.$route.params.id,
      loaded: false,
      paidFor: false,
      product: {
        price: 777.77,
        description: "leg lamp from that one movie",
        img: "./assets/lamp.jpg"
      }
    };
  },
  mounted: function() {
    const script = document.createElement("script");
    script.src =
      "https://www.paypal.com/sdk/js?client-id=AdwEwOTk25jZefu0M4_Qc7j8U7yajBFX7nBzF8DdgdzPScFukaQDMjZbbjye3nRaauR8SJ3xXfF1gV6W";
    script.addEventListener("load", this.setLoaded);
    document.body.appendChild(script);
  },
  methods: {
    setLoaded: function() {
      this.loaded = true;
      window.paypal
        .Buttons({
          createOrder: (data, actions) => {
            return actions.order.create({
              purchase_units: [
                {
                  description: this.product.description,
                  amount: {
                    currency_code: "USD",
                    value: this.product.price
                  }
                }
              ]
            });
          },
          onApprove: async (data, actions) => {
            const order = await actions.order.capture();

            this.data;

            this.paidFor = true;

            console.log(order);
          },
          onError: err => {
            console.log(err);
          }
        })
        .render(this.$refs.paypal);
    }
  }
};
</script>
<style lang="stylus" scoped>
$label = #1D0C42;

.checkout {
  background: #EEEEF1;
  position: relative;
}

.checkout-label {
  color: $label;
  font-size: 2rem;
  font-weight: 400;
}

.card-header {
  color: $label;
  font-size: 1rem;
  font-weight: 400;
}

.v-divider {
  padding: 0;
}
</style>