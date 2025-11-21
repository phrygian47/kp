<script setup lang="ts">
type Choice = "fixed" | "custom";

const selectedAmount = ref<Choice>("fixed");

const custom_amount = ref<string>("");
const amounts = ref<number[]>([5, 10, 25, 50, 100]);
</script>

<template>
  <div class="content">
    <div class="item">
      <form action="/donate" method="post">
        <!--Need to replace with donate API, including variables for each donation amount-->
        <div class="radio-btns">
          <input
            type="radio"
            id="single"
            name="donation_type"
            value="Single"
            checked
          />
          <label for="single" class="donation-type">Single Donation</label>

          <input
            type="radio"
            id="monthly"
            name="donation_type"
            value="Monthly"
          />
          <label for="monthly" class="donation-type">Monthly Donation</label>
        </div>
        <div class="form-body">
          <!-- <div class="info">
            <label class="info-label" for="first-name">First Name:</label>
            <input
              type="text"
              id="first-name"
              name="first-name"
              placeholder="First Name"
            />

            <label class="info-label" for="last-name">Last Name:</label>
            <input
              type="text"
              id="last-name"
              name="last-name"
              placeholder="Last Name"
            />

            <label class="info-label" for="email">Email:</label>
            <input type="email" id="email" name="email" placeholder="Email:" />
            <label class="info-label" for="donation">Donation:</label>
          </div> -->
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
            <input
              type="text"
              placeholder="Custom Amount"
              min="1"
              v-model.number="custom_amount"
              @focus="selectedAmount = 'custom'"
              @input="selectedAmount = 'custom'"
            />
          </div>
        </div>
        <button type="submit">Donate!</button>
      </form>
    </div>
    <div class="item">
      <div class="heading">
        <h2>Every donation builds a world harder to deceive.</h2>
        <h3>Help others to apply the Principle</h3>
      </div>
    </div>
  </div>
</template>

<style scoped>
.content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  max-height: 75%;
  height: 100%;
  padding: 2rem;
}

.heading {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
  font-size: 1.5rem;
  margin: 1rem;
}

.item {
  background-color: var(--bg-light);
  height: 100%;
  padding: 2rem;
  margin: 3rem;
}

.radio-btns {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem;
}

.radio-btns input[type="radio"] {
  display: none;
}

.donation-type {
  display: inline-block;
  padding: 0.9rem 1.3rem;
  background-color: var(--muted);
  cursor: pointer;
  font-size: 1.2rem;
}

input[name="donation_type"]:checked + .donation-type {
  background: var(--accent-amber);
  color: #fff;
  border-color: var(--accent-amber);
}

.form-body .info-label {
  display: none;
}

.info {
  margin: 0.3rem;
  display: flex;
  flex-direction: column;
}
</style>
