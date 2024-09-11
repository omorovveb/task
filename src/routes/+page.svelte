<script>
    import InputField from '$lib/components/InputField.svelte';
    import Checkbox from '$lib/components/Checkbox.svelte';
    import SubmitButton from '$lib/components/SubmitButton.svelte';
  
    let name = '';
    let company = '';
    let email = '';
    let phone = '';
    let subject = '';
    let message = '';
    let consent = false;
  
    let errors = {};
    let showNotification = false;
  
    function validateForm() {
      errors = {};
      if (!name) errors.name = 'Name is required';
      if (!company) errors.company = 'Company is required';
      if (!email || !/^[\w-]+(\.[\w-]+)*@([\w-]+\.)+[a-zA-Z]{2,7}$/.test(email)) errors.email = 'Valid email is required';
      if (!message) errors.message = 'Message is required';
      return Object.keys(errors).length === 0;
    }
  
    function handleSubmit() {
      if (validateForm()) {
        showNotification = true;
        name = '';
        company = '';
        email = '';
        phone = '';
        subject = '';
        message = '';
        consent = false;
      }
    }
  
    function handleCloseNotification() {
      showNotification = false;
    }
  </script>
  

  
  <form on:submit|preventDefault={handleSubmit}> 
     <section>
    <h3>For business enquiries please use the form below</h3>
    <p><strong>*Required</strong></p>
  </section>
    <InputField type="text" bind:value={name} placeholder="Name" error={errors.name} required={true} />
    <InputField type="text" bind:value={company} placeholder="Company" error={errors.company} required={true} />
    <InputField type="email" bind:value={email} placeholder="E-mail" error={errors.email} required={true} />
    <InputField type="tel" bind:value={phone} placeholder="Phone" />
    <InputField type="text" bind:value={subject} placeholder="Subject" />
    <InputField type="text" bind:value={message} placeholder="Message" error={errors.message} required={true} />
    <Checkbox label="I agree to the terms and conditions" bind:checked={consent} />
  
    <SubmitButton color="blue">Send</SubmitButton>
  
    {#if showNotification}
      <Notification message="Your message has been sent successfully" onClose={handleCloseNotification} />
    {/if}
  </form>
  
  <style>
    section {
      text-align: center;
      margin-bottom: 2em; 
    }
  
    h1 {
      font-size: 2em;
      color: #ffffff; 
      margin-bottom: 0.5em; 
    }
  
    p {
      font-size: 0.8em;
      color: #726e6e; 
    }
  
    strong {
      font-weight: 600; 
    }
  </style>
  