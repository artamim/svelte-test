<h1>Snippets Training</h1>
<a href="/">Back</a>
<div>
    <h2>Simple Component Example</h2>
    <p>This is a simple component example to demonstrate dynamic properties.</p>
</div>

<script lang="ts">

    // Define an interface with an index signature
    interface FormValues {
        step: number;
        name: string;
        birthday: string;
        email: string;
        phone: string;
        university: string;
        cg: string;
        error: Record<string, string>; // For error object
        [key: string]: string | number | Record<string, string>; // Index signature
    }

    let formvalues = $state<FormValues>({
        step: 1,
        name: '',
        birthday: '',
        email: '',
        phone: '',
        university: '',
        cg: '',
        error: {}
    });

    // Function to validate the current step
    /*
    let fields = [
        { header: 'Name', id: 'name', type: 'text' },
        { header: 'Birthday', id: 'birthday', type: 'date' },
        { header: 'Email', id: 'email', type: 'email' },
        { header: 'Phone', id: 'phone', type: 'tel' },
        { header: 'University', id: 'university', type: 'text' },
        { header: 'CG', id: 'cg', type: 'number' }
    ];
    
    let fields1 = [
        { header: 'Name', id: 'name', type: 'text' },
        { header: 'Birthday', id: 'birthday', type: 'date' },
        { header: 'Email', id: 'email', type: 'email' },
        { header: 'Phone', id: 'phone', type: 'tel' },
        { header: 'University', id: 'university', type: 'text' },
        { header: 'CG', id: 'cg', type: 'number' }
    ];*/
</script>

<!--Portion to do form in iteration-->

<!--
{#each fields as {header, id, type}}
    <article>
        <div>
            <label for={id}>{header}:</label>
            <input type={type} id={id} bind:value={formvalues[id]} />
        </div>
    </article>
{/each}
-->

{@render formBuilder({header: 'Name', id: 'name', type: 'text'})}
{@render formBuilder({header: 'Birthday', id: 'birthday', type: 'date'})}
{@render formBuilder({header: 'Email', id: 'email', type: 'email'})}
{@render formBuilder({header: 'Phone', id: 'phone', type: 'tel'})}
{@render formBuilder({header: 'University', id: 'university', type: 'text'})}
{@render formBuilder({header: 'CGPA', id: 'cg', type: 'number'})}

{#snippet formBuilder({header, id, type} : {header: string, id: string, type: string})}
    <article>
        <div>
            <label for={id}>{header}:</label>
            <input type={type} id={id} bind:value={formvalues[id]} />
        </div>
    </article>
{/snippet}