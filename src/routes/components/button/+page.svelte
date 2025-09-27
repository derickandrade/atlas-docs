<script lang="ts">
	import ButtonDemo from './button-demo.svelte';
</script>

<svelte:head>
	<title>Button</title>
	<meta name="Button" content="About Button Component" />
</svelte:head>

<main>
	<h1>Button</h1>
	<p>A Button triggers an action when the user clicks or taps on it.</p>
	<ButtonDemo />
	<div id="div-line"></div>
	
	<h2 id="overview">Overview</h2>

	<h3>When to use Button</h3>
	<p>Use the Button component when you want to trigger an action or toggle something in the user's current context.</p>
	<p>Avoid using Button when:</p>
	<ul class="list-dos">
		<li>The action is to navigate the user to a new resource, which would take them away from the current context. In such cases, consider Link instead. Learn more about using links and buttons.</li>
		<li>You need to represent state-persistent user actions. In this case, use ToggleButton instead.</li>
	</ul>

	<h3>About Button</h3>
	<p>Button includes the hollowing elements.</p>

	<h4>label</h4>
	<p>Button labels should be as short as possible, with text that clearly states what action follows clicking the button (e.g. download, submit form, search).</p>
	<p>Buttons labels should ideally be fewer than 38 characters in English, as translations average 42 characters. Logographic and Arabic-script languages are generally shorter, while Romance, some Germanic, Slavic, Austronesian, and others like Greek and Finnish tend to be longer, averaging 45–53 characters.</p>
	<ul class="list-dos">
		<li><span class="bold">Do:</span> Use descriptive, accessible verbs to encourage action. Concise & Accessible</li>
		<li><span class="bold">Do:</span> Write in sentence case, capitalizing only the first word. Consistent</li>
		<li><span class="bold">Do:</span> Answer direct questions in titles or body copy using the same terminology. Clear</li>
		<li><span class="bold">Don't:</span> Avoid using similar words for different actions. Clear</li>
		<li><span class="bold">Don't:</span> Avoid verbs that imply visual or sensory abilities such as "see", or are idiomatic or vague. Accessible & Translatable</li>
	</ul>


	<h4>Icon (optional)</h4>
	<p>Icons simplify user recognition and provide the ability to shorten Button labels to a minimum. When the Button includes a label, the icon is optional and should be used to add a clear visual reinforcement to the label. If the Button is icon-only, it should use a universally recognizable icon, such as the “edit” action.</p>

	<ul class="list-dos">
		<li><span class="bold">Do:</span> Ensure that icons used in buttons are relevant and easily recognizable.</li>
		<li><span class="bold">Don't:</span> Avoid using icons that are difficult to recognize or do not clearly convey their purpose.</li>
	</ul>

	<div id="div-line"></div>

	<h2 id="examples">Examples</h2>
	
	<h3>Button weight</h3>
	<p>A Button can convey one of three <span class="prop">weight</span> types.</p>

	<ol class="list-numbers">
		<li><span class="bold">Outline:</span> When designing a project, outline buttons are the default choice.</li>
		<li><span class="bold">Primary:</span> Primary buttons signal the main action in a given view – a page or a dialog. As they should guide the user to the most important action (“call to action”), there should only be one primary button per view.</li>
		<li><span class="bold">Tertiary:</span> Use quiet buttons for an easily recognizable action that does not detract focus from the content. For example, the icon-only edit buttons alongside sections in an article on mobile Wikipedia.</li>
		<li><span class="bold">Danger:</span> Reserve danger buttons for actions that involve removal or limitation, such as deleting a item or blocking a user. Avoid using them for actions like cancel buttons.</li>
	</ol>

	<h3>With icon</h3>
	<p>Use an icon with the button label when you need to convey meaning through both textual and visual elements.</p>

	<h3>Icon-only button</h3>
	<p>Use an icon-only button for actions that can be universally recognized through the icon alone. For an icon-only Button, the label is visually hidden but available to assistive technology users.</p>

	<div class="warning">Due to the lack of descriptive text, icon-only buttons require one of the following attributes: <span id="warning" class="prop">aria-label</span> or <span class="prop" id="warning">aria-hidden</span>. The attribute <span id="warning" class="prop">aria-label</span> has to be used on icon-only buttons to be understandable by assistive technology users.</div>

	<h3>Disabled button</h3>
	<p>Buttons may be disabled, but disabled buttons should be used sparingly.</p>
	<ul class="list-dos">
		<li><span class="bold">Do:</span> Use disabled Buttons when they are related to a single input, therefore implying what must be completed to enable the Button.</li>
		<li><span class="bold">Don't:</span> Avoid using disabled Buttons to prevent a user from attmepting to continue forward. Instead, rely on providing validation as a response to what might be incomplete or incorrect.</li>
	</ul>

	<h2 id="technical-implementation">Technical Implementation</h2>
	
	<div id="div-line"></div>

	<h2 id="keyboard-navigation">Keyboard Navigation</h2>
	<p>Inserir tabela</p>

	<aside>
		<ul>
            <li><a href="#overview">Overview</a></li>
            <li><a href="#examples">Examples</a></li>
            <li><a href="#technical-implementation">Technical Implementation</a></li>
			<li><a href="#keyboard-navigation">Keyboard Navigation</a></li>
        </ul>
	</aside>
</main>