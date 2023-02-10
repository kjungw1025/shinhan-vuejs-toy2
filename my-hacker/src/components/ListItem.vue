<template>
  <div>
    <!-- <div>news</div> -->
    <ol class="list">
      <li v-for="item in listData" :key="item.id">
        <b>{{ item.time_ago }}</b>

        <template v-if="$route.name === 'news'">
            <!-- to는 어디로 갈지 설정 -->
            <span>by <router-link :to="`/user/${item.user}`">{{ item.user }}</router-link></span><br/>
            <a :href="item.url">
                {{ item.title }}
            </a>
            <i><router-link :to="`item?id=${item.id}`">{{ item.comments_count }}</router-link></i>
        </template>

        <template v-else-if="$route.name === 'ask'">
            <span>by <router-link :to="`/user/${item.user}`">{{ item.user }}</router-link></span><br/>
            <router-link :to="item.url">
            {{ item.title }}
            <i>{{ item.comments_count }}</i>
            </router-link>
        </template>

        
        <template v-else>
            <span>by {{ item.user }}</span><br/>
            <a :href="item.url">
            {{ item.title }}
            <!-- <i>{{ item.comments_count }}</i> jobs에는 댓글이 없으므로 지워줌 -->
            </a>
        </template>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
    props: ['listData']
}
</script>

<style> 
</style>