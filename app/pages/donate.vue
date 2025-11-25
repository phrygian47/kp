<script setup lang="ts">
type Choice = "fixed" | "custom";

const selectedAmount = ref<Choice>("fixed");

const custom_amount = ref<string>("");
const amounts = ref<number[]>([5, 10, 25, 50, 100, 300]);
</script>

<template>
  <div class="content">
    <div class="item">
      <div class="heading">
        <h2>
          Stop <br />
          Manipulation <br />
          Today
        </h2>
      </div>
      <div class="subheading">
        <h3>
          Misinformation has become a common strategy, with more than 93% of the
          countries seeing it deployed as part of political communication.
        </h3>
      </div>
    </div>
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
        <div class="subtitle"><h3>Choose an amount to donate</h3></div>
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
          <div class="donation-amounts">
            <div
              class="donation-amount-item"
              v-for="amount in amounts"
              :key="amount"
            >
              <input
                type="radio"
                name="donation_amount"
                :id="`donation-${amount}`"
                :value="amount"
                v-model="selectedAmount"
              />
              <label class="donation-amount" :for="`donation-${amount}`">
                ${{ amount }}
              </label>
            </div>
          </div>

          <!-- Custom amount -->
          <div class="custom-amount">
            <input
              type="radio"
              name="donation_amount"
              id="donation-custom"
              value="custom"
              v-model="selectedAmount"
            />
            <input
              type="number"
              placeholder="Custom Amount"
              step="0.01"
              min="1"
              v-model.number="custom_amount"
              @focus="selectedAmount = 'custom'"
              @input="selectedAmount = 'custom'"
            />
          </div>
        </div>
        <div class="submit">
          <button class="submit-btn" type="submit">DONATE</button>
        </div>
      </form>
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
  letter-spacing: 1px;
  font-size: 3.5rem;
  margin: 1rem;
  text-transform: uppercase;
}

.subheading {
  text-align: justify;
  width: 50%;
  font-size: 1rem;
  margin: 1rem;
  font-family:
    "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
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
  font-family:
    "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}

input[type="radio"] {
  display: none;
  cursor: pointer;
}

.donation-type {
  display: inline-block;
  padding: 0.9rem 1.3rem;
  background-color: #fff;
  cursor: pointer;
  font-size: 1.3rem;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
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

.subtitle {
  display: flex;
  justify-content: center;
  align-items: center;
  font-family:
    "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}

.donation-amounts {
  margin: 0 auto;
  width: 60%;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 0.2rem;
}

.donation-amount-item {
  display: flex;
  justify-content: center;
  width: 100%;
}

.donation-amount {
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0.2rem;
  padding: 0.9rem 1.3rem;
  cursor: pointer;
  font-size: 1.2rem;
  border-radius: 0.5rem;
  border: 2px solid var(--muted);
  width: 100%;
  font-size: 1.3rem;
  font-weight: 600;
  font-family: sans-serif;
  background-color: #fff;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}

/* when a donation_amount radio is checked, style its label */
input[name="donation_amount"]:checked + .donation-amount {
  background: var(--accent-amber);
  color: #fff;
  border-color: var(--accent-amber);
}

.custom-amount {
  position: relative;
  display: inline-block;
  margin: 0 auto;
  font-size: 1.3rem;
}

.form-body {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

input[type="number"] {
  outline-style: solid;
  outline-color: var(--muted);
  border: none;
  border-radius: 0.5rem;
  -moz-appearance: textfield;
  padding: 0.9rem 1.1rem;
  padding-left: 2rem;
}

.custom-amount::before {
  position: absolute;
  content: "$";
  left: 0.75rem;
  top: 50%;
  transform: translateY(-50%);
  color: var(--muted);
  pointer-events: none;
}

.custom-amount:focus-within::before {
  color: #000;
}

input[type="number"]:focus {
  outline: none;
  outline-style: solid;
  outline-color: var(--accent-amber);
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

.submit-btn {
  padding: 0.9rem 1.1rem;
  margin-top: 5rem;
  font-size: 1.3rem;
  background-color: var(--accent-amber);
  border: none;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
  color: #fff;
  font-weight: 600;
  font-family:
    "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  letter-spacing: 1px;
  border-radius: 0.5rem;
  width: 40%;
  cursor: pointer;
}

.submit {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
