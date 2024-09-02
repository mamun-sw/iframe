<script>
	const urlSingleAddress = 'https://stagingapp.propcloud.no/#/valuation/4001/46/432'
	const urlMultipleAddress = 'https://stagingapp.propcloud.no/#/valuation/0301/214/427'

	let iframe;

	function loadIframe(iframeSrc, dataToSend) {
			iframe.src = iframeSrc;

			iframe.style.width = '100%';
			iframe.style.height = '100%';

			iframe.onload = function() {
					iframe.contentWindow.postMessage(dataToSend, iframeSrc);
			};
	}

	let dialog;

	const openDialog = (url) => {
		const data = {
			key: "Hello Placepoint!"
		}
		loadIframe(url, data);

		dialog?.showModal();
	};

	const closeDialog = () => {
		dialog?.close();

		// destroy iframe
		iframe.src = '';
	};

</script>


<section >
	<button class="mybutton" on:click={()=>openDialog(urlSingleAddress)}>
		Propcloud valuation page (Single Unit)
	</button>
	<button class="mybutton" on:click={()=>openDialog(urlMultipleAddress)}>
		Propcloud valuation page (Multiple Unit)
	</button>


	<dialog bind:this={dialog} class=" w-[1000px] h-[700px] rounded-xl border overflow-hidden">
		<div class="h-12 bg-white border-b flex justify-end items-center px-6">
			<button class=" bg-slate-500 p-1 px-2 text-sm hover:bg-slate-500/80 text-white rounded-lg" on:click={closeDialog}>Close</button>
		</div>
		<div class="h-[calc(100%-3rem)] w-full overflow-y-auto">
			<iframe bind:this={iframe} title="valuation" frameborder="0"></iframe>
		</div>
	</dialog>

</section>


<style>
	section{
		display: flex;
		justify-content: center;
	}

	.mybutton{
		padding: 10px 20px;
		margin: 10px;
		height: auto;
		width: auto;
		font-size: 1rem;
		border: none;
		border-radius: 5px;
		background-color: #007bff;
		color: white;
		cursor: pointer;
	}

	.mybutton:hover{
		background-color: #0056b3;
	}
</style>
