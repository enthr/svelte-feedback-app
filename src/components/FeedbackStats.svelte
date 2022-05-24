<script>
    import { FeedbackStore } from "../stores";

    $: count = $FeedbackStore.length;
    $: avg = $FeedbackStore.reduce((acc, item) => acc + item.rating, 0) / $FeedbackStore.length;
</script>

<div class="feedback-stats">
    <h4>{count} Reviews</h4>
    <h4>Average Rating: {avg} / 10</h4>
</div>

<style>
    .feedback-stats {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>
