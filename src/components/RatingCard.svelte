<div class={`RatingCard-comp comp ${customClass}`}>
    <div class="star-container">
        {#each [...Array(rating).keys()] as _}
            <img src="./assets/icon-star.svg" alt="star" />
        {/each}
    </div>
    <p>Rated {rating} {rating > 1 ? "stars" : "star"} in {source}</p>
</div>

<script>
export let rating = 0
export let source = ""
export let customClass = ""
</script>

<style type="text/scss">
@import "../shared"; 
.RatingCard-comp {
    display: flex;
    gap: 30px;
    align-items: center;
    .star-container {
        display: flex;
        gap: 5px;
    }
    p {
        font-weight: 600;
        color: hsl(300, 43%, 22%);
        height: 13px;
    }
}
@include media(">tablet") {
    .RatingCard-comp {
        .star-container {
            img {
                width: mathFromPcToTablet(17,12);
                height: mathFromPcToTablet(16,11);
            }
        }
        p {
            font-size: mathFromPcToTablet(14,13);
        }
    }
}
@include media("<=tablet") {
    .RatingCard-comp {
        flex-direction: column;
        width: fit-content;
        gap: 15px;
        font-size: 17px;
    }
}
</style>