<script>
    import { onMount } from 'svelte';
    import Talk from 'talkjs';

    onMount(() => {
    Talk.ready.then(() => {
        const session = new Talk.Session({
        appID: 'YOUR_APP_ID',
        me: currentUser,
    });
  });
});

const currentUser = new Talk.User({
  id: '1920',
  name: 'Oliver Johnson',
  email: 'oliverjohnson@example.com',
  photoUrl: 'oliver.jpeg',
  welcomeMessage: 'Hey there!',
  role: 'default',
});

const otherUser = new Talk.User({
  id: '2017',
  name: 'Abby Klein',
  email: 'abbyklein@example.com',
  photoUrl: 'abby.jpeg',
  welcomeMessage: 'Hello, how are you today?',
  role: 'default',
});

const conversation = session.getOrCreateConversation(
  Talk.oneOnOneId(currentUser, otherUser)
);

conversation.setParticipant(currentUser);
conversation.setParticipant(otherUser);

const chatbox = session.createChatbox();
chatbox.select(conversation);
chatbox.mount(chatboxEl);

  let chatboxEl;
  </script>

<main>
    <div bind:this={chatboxEl}></div>
  </main>