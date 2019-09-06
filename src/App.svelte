<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "";
  let title = "";
  let image = "https://i.pravatar.cc/125";
  let description = "";
  let formState = "empty";

  let createdContacts = [];
  function addContact() {
    if (
      (name.trim(),
      length == 0 ||
        title.trim().length == 0 ||
        image.trim().length == 0 ||
        description.trim().length == 0)
    ) {
      formState = "invalid";
      return;
    } else {
      createdContacts = [...createdContacts,{
        name: name,
        jobTitle: title,
        imageUrl: image,
        desc: description
      }];
      formState = "done";
      return;
    }
  }
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>

<div id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value={image} id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc" />
  </div>
  <button on:click={addContact}>Add Contact</button>
</div>
<br />
<hr />
{#if formState === 'invalid'}
  <p>error</p>
{:else}
  <p>please enter some data</p>
{/if}

{#each createdContacts as contact, index}
  <p>#{index+1}</p>
<ContactCard
    userName={contact.name}
    jobPosition={contact.jobTitle}
    userDescription={contact.desc}
    imageUrl={contact.imageUrl} />
{:else}
  <p>please start adding some contacts</p>
{/each}