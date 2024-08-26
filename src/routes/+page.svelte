<script>
		
	const main = 'http://localhost:5173/#/valuation/0301/214/427';
	const unit = `http://localhost:5173/#/valuation/4001/382/98/0/0/6266364028`;

	function handleClick(url) {
			const data = {
				key: "Hello Placepoint!"
			}
			openWindowWithIframe(url, data);
	}


	function openWindowWithIframe(iframeSrc, dataToSend) {
			const newWindow = window.open('', '_blank', 'popup');

			const iframe = document.createElement('iframe');
			iframe.src = iframeSrc;

			iframe.style.width = '100%';
			iframe.style.height = '100%';
			iframe.style.border = 'none';
			iframe.style.overflow = 'hidden';
			iframe.style.position = 'fixed';
			iframe.style.top = '0';
			iframe.style.left = '0';
			iframe.style.right = '0';
			iframe.style.bottom = '0';
			
			
			newWindow.document.body.appendChild(iframe);

			iframe.onload = function() {
					iframe.contentWindow.postMessage(dataToSend, iframeSrc);
			};
	}

</script>


<section >

	<button on:click={()=>handleClick(main)}>
		Propcloud valuation page (Main)
	</button>

	<button on:click={()=>handleClick(unit)}>
		Propcloud valuation page (Unit)
	</button>
</section>


<style>
	section{
		display: flex;
		justify-content: center;
	}

	button{
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

	button:hover{
		background-color: #0056b3;
	}
</style>
