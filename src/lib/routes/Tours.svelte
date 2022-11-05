<script lang="ts">
  import { onMount } from "svelte";
  import App from "../App.svelte";

  import { toursList, toursData } from "../assets/data";

  let tours = [];
  let isToursLoading = true;
  let selectedTour = undefined;
  let tourSearch = "";

  $: tourSearchLowerCased = tourSearch.toLowerCase();
  $: filteredList = tours.filter(({ title }) =>
    title.toLowerCase().includes(tourSearchLowerCased)
  );

  onMount(async () => {
    const promise = new Promise((res) => {
      setTimeout(() => res(toursList), 1);
    });

    tours = (await promise) as any;
    isToursLoading = false;
  });

  const selectTour = (id) => {
    selectedTour = id;
  };
</script>

{#if isToursLoading}
  <div>Loading...</div>
{:else}
  <div class="tours">
    <div class="tours-list__wrap">
      <input
        bind:value={tourSearch}
        class="tours-list__item-search"
        type="search"
        placeholder="Search for a tour"
      />
      <div class="tours-list">
        {#each filteredList as tour}
          <button class="tours-list__item" on:click={() => selectTour(tour.id)}>
            <img
              alt="Tour preview"
              src={tour.image}
              class="tours-list__item-image"
            />
            <div>{tour.title}</div>
          </button>
        {/each}
      </div>
    </div>
    <div class="selected-tour">
      {#if selectedTour}
        <div class="selected-tour__content">
          <h2>{toursData[selectedTour].title}</h2>
          <div class="selected-tour__meta-info">
            <div class="selected-tour__price">
              {toursData[selectedTour].price}$
            </div>
            <div class="selected-tour__marks">
              {toursData[selectedTour].reviewersAmount} reviews
              <div
                class="stars"
                style={`
                  background-image: linear-gradient(90deg, gold ${
                    (toursData[selectedTour].mark / 5) * 100
                  }%, grey ${(toursData[selectedTour].mark / 5) * 100}%)
                  `}
              >
                ★★★★★
              </div>
            </div>
          </div>
          <p>{toursData[selectedTour].about}</p>
        </div>
      {:else}
        <div class="selected-tour__select-message">
          Select a tour to view more info about it
        </div>
      {/if}
    </div>
  </div>
{/if}

<style>
  .tours {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
  }

  .tours-list__wrap {
    min-width: 30%;
    max-width: 30%;
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
  }

  .tours-list {
    border-right: 1px solid rgb(230, 230, 230);
  }

  .tours-list__item-search {
    width: 100%;
    background: none;
    border: 1px solid rgb(230, 230, 230);
    padding: 8px;
    box-sizing: border-box;
    border-radius: 8px;
    margin-bottom: 24px;
  }

  .tours-list__item {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    min-width: 100%;
    background: none;
    border: none;
    border-radius: 0px;
    padding: 8px;
    height: 86px;
    font-weight: 600;
    text-align: left;
    border-bottom: 1px solid rgb(230, 230, 230);
  }

  .tours-list__item:hover {
    background: rgb(230, 230, 230);
    cursor: pointer;
  }

  .tours-list__item:last-child {
    border-bottom: none;
  }

  .tours-list__item-image {
    max-height: 100%;
    max-width: 30%;
    border-radius: 4px;
    margin-right: 8px;
  }

  .selected-tour {
    padding: 52px 24px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    min-width: 70%;
    max-width: 70%;
    box-sizing: border-box;
  }

  .selected-tour h2 {
    margin-top: 0px;
    height: 55px;
  }

  .selected-tour__meta-info {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }

  .selected-tour__price {
    font-weight: 600;
  }

  .selected-tour__marks {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .stars {
    display: flex;
    flex-direction: row;
    align-items: center;
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }
</style>
