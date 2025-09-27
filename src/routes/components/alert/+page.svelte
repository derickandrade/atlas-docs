<svelte:head>
	<title>Alert</title>
	<meta name="Alert" content="Alert component" />
</svelte:head>

<main>
	<h1>Alert</h1>
	<p>
		The Alert component is designed to deliver system information to users in an explicit and noticeable manner. It supports various use cases including feedback delivery, warnings, and error reporting, with display options ranging from standalone messages to inline form validation feedback.	
	</p>
    <img src="" alt="Imagem dos alertas" />
    <div id="div-line"></div>

    <h2 id="overview">Overview</h2>

    <h3>When to use Alert</h3>
    <p>
        <span class="semibold">Use the Alert component to display system feedback, respond to user actions, or provide information.</span> Use <span class="semibold"> inline alert</span> to provide feedback on form input validation.  
        Depending on the type of feedback conveyed to the user, <span class="semibold">Alerts</span> can be used to communicate one of four statuses:
    </p>
    <ul class="list-dos">
        <li>
            <span class="bold">Info:</span> Use to provide general, neutral, and non-urgent information or recommendations.
        </li>
        <li>
            <span class="bold">Warning:</span> Use to provide important information about situations that require caution.
        </li>
        <li>
            <span class="bold">Error:</span> Use to alert the user only in situations that require immediate attention. <span class="semibold">Error Alerts</span> have the strongest visual priority among all system messages.
        </li>
        <li>
            <span class="bold">Success:</span> Use to provide feedback about a successful user interaction, such as publishing an article.
        </li>
    </ul>

    <div class="note">When recommending against using a component, always suggest alternative components to guide users effectively.</div>

    <h3>About Alerts</h3>
    <p>Alerts includes the following elements.</p>

    <h4>Icon</h4>
    <p>Icons enhance user recognition and allow for more concise messaging. Each message type (e.g., "success") is paired with a distinct icon to ensure quick identification.</p>

    <h4>Alert Text</h4>
    <p>The alert text should be as clear and concise as possible, providing feedback to users. If applicable, it may also suggest next steps.</p>
    <p>
        Keep messages <span class="semibold">short and simple</span>, offering one or two solutions to reduce cognitive load.
    </p>
    
    <ul class="list-dos">
        <li>
            <span class="bold">Do:</span> Concise & Accessible: Incorporate various text formats and links within the message text as needed. 
        </li>

        <li>
            <span class="bold">Don't:</span> Avoid bolding the entire message text.
        </li>
    </ul>

    <h3>Close button (optional)</h3>
    <p>To allow the message to be dismissed, an optional icon-only quiet button can be included.</p>

    <h2 id="examples">Examples</h2>
    <h3>Fade in</h3>
    <p>A transition effect can be applied when a <span class="semibold">Alert</span> is dynamically added to the user interface.</p>

    <h3>Dismiss button</h3>
    <p><span class="semibold">Alerts</span> can be dismissed using the close button within the Alert component. Note that inline messages cannot be dismissed.</p>

    <img src="" alt="Imagem com dismiss button">

    <h3>Auto-dismiss</h3>
    <p><span class="semibold">Alerts</span> can be auto-dismissable. Auto-dismiss can be used with or without the manual dismiss button.</p>

    <ul class="list-dos">
        <li>
            <span class="bold">Do:</span> Use for very short Alerts to ensure that they can be read and understood before disappearing. 
        </li>

        <li>
            <span class="bold">Don't:</span> Avoid using with error Alerts to prevent the message from disappearing before users fix the error.
        </li>
    </ul>

    <div id="div-line"></div>

    <h3 id="multiline">Multiline</h3>
    <p><span class="semibold">Alerts</span> can be dismissed using the close button within the Alert component. Note that inline messages cannot be dismissed.</p>

    <img src="" alt="Imagem com multiline">

    <h3>With custom icon</h3>
    <p>Only info Alerts may have a custom icon.</p>

    <img src="" alt="Imagem com custom icon">

    <h2 id="technical-implementation">Technical Implementation</h2>
    <h3>Props</h3>
    <p>Inserir a tabela</p>

    <h3>Extended Props (Optional Enhancements)</h3>
    <p>Inserir a tabela</p>

    <h3>Keyboard navigation</h3>
    <p>Inserir a tabela</p>
    <img src="" alt="">

	<aside>
		<ul>
            <li><a href="#overview">Overview</a></li>
            <li><a href="#examples">Examples</a></li>
            <li><a href="#multiline">Multiline</a></li>
            <li><a href="#technical-implementation">Technical Implementation</a></li>
        </ul>
	</aside>
	
</main>
