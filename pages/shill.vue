<template>
  <Head>
    <Title>Shill and discuss projects | {{ $config.projectMetadataTitle }}</Title>
    <Meta property="og:title" :content="'Shill and discuss projects | ' + $config.projectMetadataTitle" />
  </Head>

  <ChatFeed 
    class="mt-1" 
    :showQuotedPost="$config.showRepliesOnHomepage" 
    :allPosts="true" 
    orbisContext="kjzl6cwe1jw146ryuc6m63h5l542wwde6fmza8xu91okwn9hz9nf76ae109yq4r" 
  />
</template>

<script>
import { useEthers } from 'vue-dapp'
import ChatFeed from "../components/chat/ChatFeed.vue"

export default {
  name: "shill",

  components: {
    ChatFeed
  },

  computed: {
    getOrbisContext() {
      if (this.$config.orbisTest) {
        return this.$config.orbisTestContext;
      } else {
        return this.$config.orbisContext;
      }
    }
  },

  setup() {
    const { address, chainId } = useEthers()

    return { address, chainId }
  }
}
</script>