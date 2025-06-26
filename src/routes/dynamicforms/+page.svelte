<h1>Dynamic Form Training</h1>
<a href="/">Back</a>

<script lang="ts">
    type ErrorFields = {
        [key: string]: string;
        name: string;
        birthday: string;
        email: string;
        phone: string;
        university: string;
        cg: string;
    };
    
    // Initial form values
    let formvalues = {
        name: '',
        birthday: '',
        email: '',
        phone: '',
        university: '',
        cg: 0.00,
        error: {
            name: '',
            birthday: '',
            email: '',
            phone: '',
            university: '',
            cg: ''
        } as ErrorFields,
        step: 1
    };

    // Dynamic validation function
    function validateStep(fields: { key: string, value: string | number | Date, label: string }[]) {
        let isValid = true;
        // Reset errors for all fields
        formvalues.error = { ...formvalues.error };

        fields.forEach(field => {
            if (typeof field.value === 'string' && !field.value.trim()) {
                formvalues.error[field.key] = `${field.label} is required`;
                isValid = false;
            } else if (typeof field.value === 'number' && field.value <= 0) {
                formvalues.error[field.key] = `${field.label} must be greater than 0`;
                isValid = false;
            } else if (field.value instanceof Date && isNaN(field.value.getTime())) {
                formvalues.error[field.key] = `${field.label} is invalid`;
                isValid = false;
            } else {
                formvalues.error[field.key] = '';
            }
        });

        return isValid;
    }
</script>

<div>
    {#if formvalues.step === 1}
        <h2>Step 1: Personal Information</h2>
        <div>
            <input type="text" placeholder="Enter your name" bind:value={formvalues.name}/>
            {#if formvalues.error.name}
                <p style="color: red">{formvalues.error.name}</p>
            {/if}
        </div>
        <div>
            <input type="date" placeholder="Enter your birthDate" bind:value={formvalues.birthday}/>
            {#if formvalues.error.birthday}
                <p style="color: red">{formvalues.error.birthday}</p>
            {/if}
        </div>
        <div>
            <input type="email" placeholder="Enter your email" bind:value={formvalues.email}/>
            {#if formvalues.error.email}
                <p style="color: red">{formvalues.error.email}</p>
            {/if}
        </div>
        <div>
            <input type="tel" placeholder="Enter your phone number" bind:value={formvalues.phone}/>
            {#if formvalues.error.phone}
                <p style="color: red">{formvalues.error.phone}</p>
            {/if}
        </div>
        <button on:click={() => {
            if (validateStep([
                { key: 'name', value: formvalues.name, label: 'Name' },
                { key: 'email', value: formvalues.email, label: 'Email' },
                { key: 'birthday', value: formvalues.birthday, label: 'Birthday' },
                { key: 'phone', value: formvalues.phone, label: 'Phone number' }
            ])) {
                formvalues.step = 2;
            }
        }}>Next</button>
    {:else if formvalues.step === 2}
        <h2>Step 2: Academic Information</h2>
        <div>
            <input type="text" placeholder="Enter your university" bind:value={formvalues.university}/>
            {#if formvalues.error.university}
                <p style="color: red">{formvalues.error.university}</p>
            {/if}
        </div>
        <div>
            <input type="number" placeholder="Enter your CGPA" bind:value={formvalues.cg}/>
            {#if formvalues.error.cg}
                <p style="color: red">{formvalues.error.cg}</p>
            {/if}
        </div>
        <button on:click={() => {
            if (validateStep([
                { key: 'university', value: formvalues.university, label: 'University' },
                { key: 'cg', value: formvalues.cg, label: 'CGPA' }
            ])) {
                formvalues.step = 3;
            }
        }}>Next</button>
        <button on:click={() => formvalues.step = 1}>Previous</button>
    {:else if formvalues.step === 3}
        <h2>Review Your Information</h2>
        <p>Name: {formvalues.name}</p>
        <p>Birthday: {formvalues.birthday}</p>
        <p>Email: {formvalues.email}</p>
        <p>Phone: {formvalues.phone}</p>
        <p>University: {formvalues.university}</p>
        <p>CGPA: {formvalues.cg}</p>
        <button on:click={() => formvalues.step = 1}>Edit</button>
    {/if}
</div>