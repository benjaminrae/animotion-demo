<script lang="ts">
	export const preload = true
	import { Action, Code, Presentation, Slide } from '@animotion/core'

	let slide1: Code
	let slide2: Code
	let slide3: Code
	let slide4: Code
	let slide5: Code
	let slide6: Code
</script>

<Presentation options={{history: true, transition: 'fade', controls: true, progress: true}}>
	<Slide class="h-full place-content-center place-items-center">
		<Code bind:this={slide1} lang="ts" theme="synthwave-84"
					options={{duration: 600, stagger: 0.3, containerStyle: false}}
					code={
						`render(<ProductForm />);

						const input = screen.getByLabelText("Product Name");

						expect(input).toBeVisible();`} />

		<Action do={() => slide1.selectLines`3`} />
		<Action do={() => {
			slide1.update
				`render(<ProductForm />);

				// This will throw an error if the element is not found
				const input = screen.getByLabelText("Product Name");

				expect(input).toBeVisible();`
		slide1.selectLines`3,4`}} />
	</Slide>

	<Slide class="h-full place-content-center place-items-center">
		<Code class="h-full" bind:this={slide2} lang="ts" theme="synthwave-84"
					options={{duration: 600, stagger: 0.3, containerStyle: false}}
					code={
							`render(<ProductForm />);

							const input = screen.queryByLabelText("Product Name");

							expect(input).toBeVisible();`} />

		<Action do={() => slide2.selectLines`3`} />
		<Action do={() => {
			slide2.update
				`render(<ProductForm />);

				// This will throw an error if the element is not found
				const input = screen.queryByLabelText("Product Name");

				expect(input).toBeVisible();`
			slide2.selectLines`3,4`
		}} />
		<Action do={() => {
			slide2.update
				`render(<ProductForm />);

				// This will throw an error if the element is not found
				// It's recommended to only use queryBy to check for the absence of an element
				const input = screen.queryByLabelText("Product Name");

				expect(input).not.toBeInTheDocument();`
			slide2.selectLines`3-7`
			}} />
	</Slide>

	<Slide class="h-full place-content-center place-items-center">
		<Code class="h-full" bind:this={slide3} lang="ts" theme="synthwave-84"
					options={{duration: 600, stagger: 0.3, containerStyle: false}}
					code={
							`render(<ProductForm />);

							const input = await screen.findByLabelText("Product Name");

							expect(input).toBeVisible();`} />

		<Action do={() => slide3.selectLines`3`} />
		<Action do={() => {
			slide3.update
				`render(<ProductForm />);

				// This will try for 1000ms to find the element and then throw an error
				const input = await screen.findByLabelText("Product Name");

				expect(input).toBeVisible();`
			slide3.selectLines`3,4`
			}} />
	</Slide>

	<Slide class="h-full place-content-center place-items-center">
		<Code class="h-full" bind:this={slide4} lang="ts" theme="synthwave-84"
					options={{duration: 600, stagger: 0.3, containerStyle: false}}
					code={
							`render(<ProductForm />);

							const input = await waitFor(() => screen.getByLabelText("Product Name"));

							expect(input).toBeVisible();`} />

		<Action do={() => slide4.selectLines`3`} />
		<Action do={() => {
			slide4.update
				`render(<ProductForm />);

				// Don't wrap getBy calls in a waitFor
				const input = await waitFor(() => screen.getByLabelText("Product Name"));

				expect(input).toBeVisible();`
			slide4.selectLines`3,4`}} />
		<Action do={() => {
			slide4.update
				`render(<ProductForm />);

				// Instead use findBy (it already includes a waitFor)
				const input = await screen.findByLabelText("Product Name");

				expect(input).toBeVisible();`
			slide4.selectLines`3,4`}} />
	</Slide>

	<Slide class="h-full place-content-center place-items-center">
		<Code class="h-full" bind:this={slide5} lang="ts" theme="synthwave-84"
					options={{duration: 600, stagger: 0.3, containerStyle: false}}
					code={
							`render(<ProductForm />);

							const input = screen.getByLabelText("Product Name");

							fireEvent.change(input, "Television");`} />

		<Action do={() => slide5.selectLines`5`} />
		<Action do={() => {
			slide5.update
							`render(<ProductForm />);

							const input = screen.getByLabelText("Product Name");

							// Don't use fireEvent unless you have a good reason to
							fireEvent.change(input, "Television");`
			slide5.selectLines`5,6`}} />
		<Action do={() => {
			slide5.update
				`render(<ProductForm />);

							const input = screen.getByLabelText("Product Name");

							// Use userEvent instead to simulate user interactions
							await userEvent.type(input, "Television");`
			slide5.selectLines`5,6`}} />
		<Action do={() => {
			slide5.update
				`render(<ProductForm />);

							const input = screen.getByLabelText("Product Name");

							// Use userEvent instead to simulate user interactions
							// It represents the way a user would interact with the element
							// Instead of just firing an onChange event, it will also trigger other important events such as focus
							await userEvent.type(input, "Television");`
			slide5.selectLines`5-8`}} />
	</Slide>

	<Slide class="h-full place-content-center place-items-center">
		<Code class="h-full" bind:this={slide6} lang="ts" theme="synthwave-84"
					options={{duration: 600, stagger: 0.3, containerStyle: false}}
					code={
							`render(<ProductForm />);

							const input = screen.getByLabelText("Product Name");

							expect(input).toBeInTheDocument();`} />

		<Action do={() => slide6.selectLines`5`} />
		<Action do={() => {
			slide6.update
							`render(<ProductForm />);

							const input = screen.getByLabelText("Product Name");

							// toBeInTheDocument only checks if the element is in the DOM
							expect(input).toBeInTheDocument();`
			slide6.selectLines`5,6`}} />
		<Action do={() => {
			slide6.update
				`render(<ProductForm />);

				const input = screen.getByLabelText("Product Name");

				// toBeInTheDocument only checks if the element is in the DOM
				// Use toBeVisible to check if the element is visible to the user
				expect(input).toBeVisible();`
			slide6.selectLines`5-7`}} />
		<Action do={() => {
			slide6.update
				`render(<ProductForm />);

				const input = screen.getByLabelText("Product Name");

				// toBeInTheDocument only checks if the element is in the DOM
				// Use toBeVisible to check if the element is visible to the user
				// Use .not.toBeInTheDocument() to check if the element is not in the DOM
				expect(input).not.toBeInTheDocument();`
			slide6.selectLines`5-8`}} />
	</Slide>

</Presentation>