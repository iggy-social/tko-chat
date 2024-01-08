<template>
  <Head>
    <Title>Shill and discuss projects | {{ $config.projectMetadataTitle }}</Title>
    <Meta property="og:title" :content="'Shill and discuss projects | ' + $config.projectMetadataTitle" />
  </Head>

  <ChatFeed 
    class="mt-1" 
    :showQuotedPost="$config.showRepliesOnHomepage" 
    :allPosts="true" 
    orbisContext="kjzl6cwe1jw14bbfcpyha0lk1q3nrb1suoec3edma8i8b0g0lbyh73bl57igwlr" 
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