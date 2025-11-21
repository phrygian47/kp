<script setup lang="ts">
type Choice = "fixed" | "custom";

const selectedAmount = ref<Choice>("fixed");

const custom_amount = ref<number>(0);
const amounts = ref<number[]>([5, 10, 25, 50, 100]);
</script>

<template>
  <div class="content">
    <div class="item">
      <h2>Every donation builds a world harder to deceive.</h2>
      <h3>Help others to apply the Principle</h3>
      <form action="/donate" method="post">
        <!--Need to replace with donate API-->
        <div class="radio-btns">
          <label for="single">Single Donation</label><br />
          <input type="radio" id="single" name="donation_type" value="Single" />

          <label for="monthly">Monthly Donation</label><br />
          <input
            type="radio"
            id="monthly"
            name="donation_type"
            value="Monthly"
          />
        </div>
        <div class="form-body">
          <label for="first-name">First Name:</label>
          <input
            type="text"
            id="first-name"
            name="first-name"
            placeholder="First Name"
          />

          <label for="last-name">Last Name:</label>
          <input
            type="text"
            id="last-name"
            name="last-name"
            placeholder="Last Name"
          />

          <label for="email">Email:</label>
          <input type="email" id="email" name="email" placeholder="Email:" />
          <label for="donation">Donation:</label>

          <!-- Preset amounts -->
          <div class="donation-amounts" v-for="amount in amounts" :key="amount">
            <input
              type="radio"
              name="donation_amount"
              :id="`donation-${amount}`"
              :value="amount"
              v-model="selectedAmount"
            />
            <label :for="`donation-${amount}`"> ${{ amount }} </label>
          </div>

          <!-- Custom amount -->
          <div>
            <input
              type="radio"
              name="donation_amount"
              id="donation-custom"
              value="custom"
              v-model="selectedAmount"
            />
            <label for="donation-custom">
              Custom Amount
              <input
                type="text"
                min="1"
                v-model.number="custom_amount"
                @focus="selectedAmount = 'custom'"
                @input="selectedAmount = 'custom'"
              />
            </label>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>
