<template>
  <Head>
    <Title>Memes & NFTs | {{ $config.projectMetadataTitle }}</Title>
    <Meta property="og:title" :content="'Memes & NFTs | ' + $config.projectMetadataTitle" />
  </Head>

  <ChatFeed 
    class="mt-1" 
    :showQuotedPost="$config.showRepliesOnHomepage" 
    :allPosts="true" 
    orbisContext="kjzl6cwe1jw146cone6md8rij8pe51xa33gyxyz599l2k4aadl4p6j990af1gxt" 
  />
</template>

<script>
import { useEthers } from 'vue-dapp'
import ChatFeed from "../components/chat/ChatFeed.vue"

export default {
  name: "memesnfts",

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