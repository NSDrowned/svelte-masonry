<script>
	import { afterUpdate } from 'svelte';

	export let id;
	export let title;
	export let width;
	
	var gridrowend;
	let height = Math.floor(Math.random() * 100 + 50);

    function resizeGridItem(item){
		var grid = document.getElementById('grid');
		var item = document.getElementById(id);
        var rowHeight = parseInt(window.getComputedStyle(grid).getPropertyValue('grid-auto-rows'));
        var rowGap = parseInt(window.getComputedStyle(grid).getPropertyValue('grid-row-gap'));
        var rowSpan = Math.ceil((item.getBoundingClientRect().height + rowGap) / (rowHeight + rowGap));
		gridrowend = "span " + rowSpan;
    }	

	afterUpdate(() => {
		resizeGridItem();
	});

    let userIsLogged;
    let threadStatus = 1;
    let threadText = "What's the name of this pornstar?";
    let threadAnswer;
    let shortThreadAnswer;
    let threadExtraPoints = 2;
    let threadCommentCount = 2;
    let postIcon = id + " - " + title;
    let favoritedClasses;
	let threadThumb;
	
</script>

<style type="text/sass">
	@import './postbit.scss';
</style>

<div class="postbit" id={id} data-thread={id} style="width: {width}px; height: {height}px; grid-row-end: {gridrowend}">

	{#if threadText && !threadAnswer}
	<div class="postbit__title">{id}</div>
	{/if}
	<div class="postbit__answer">
		<div class="postbit__answer--highlight">ANSWER:</div>
		<div class="postbit__answer--text">{shortThreadAnswer}</div>
	</div>

</div>