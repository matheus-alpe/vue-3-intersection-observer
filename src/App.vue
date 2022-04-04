<script setup>
import { ref, onMounted } from 'vue'

const headers = [
    'Section 1',
    'Section 2',
    'How this works with long long long long long sections titles?',
    'Section 4',
    'Section 5'
]

const currentSection = ref('')

const entriesHandler = (entries) => {
    entries.forEach((entry) => {
        if (entry.intersectionRatio > 0) {
            currentSection.value = entry.target.getAttribute('id')
        }
    })
}

onMounted(() => {
    const observer = new IntersectionObserver(entriesHandler, { rootMargin: '0px 0px -90% 0px'})

    document.querySelectorAll('article h2').forEach((section) => {
        observer.observe(section)
    })
})
</script>

<template>
    <main>
        <article>
            <h1>My Article</h1>
            <section v-for="(header, index) in headers" :key="header">
                <h2 :id="index">{{ header }}</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Deserunt labore aliquid, laborum, veritatis fugit quisquam quam tempore incidunt culpa earum nobis ullam. Ad architecto quia est soluta aperiam velit quaerat aliquid dolore, neque nulla ab eaque enim unde praesentium dignissimos non consectetur voluptatibus corrupti exercitationem explicabo doloribus quas consequuntur distinctio? Corporis rem quos eos provident quam saepe consectetur, numquam nulla veritatis perferendis. Libero, blanditiis. Facilis provident excepturi nam natus aspernatur libero odio culpa corporis inventore porro delectus, dolore, hic suscipit? Tempora perspiciatis unde eius molestias numquam ad facere officiis quam rerum et provident, temporibus quae. Esse unde voluptate nulla omnis, delectus iure, sint quos aliquam sunt ea dignissimos. Sapiente saepe error iste unde perspiciatis molestias vitae reprehenderit neque adipisci commodi laboriosam nemo fugit officiis eligendi cupiditate, ipsa cum velit quae eos maiores cumque ducimus. Animi nisi unde porro. Vero rem iusto corporis omnis et, ea cum deserunt magni eaque, praesentium iure perferendis molestiae possimus! Ducimus animi consequuntur, eligendi, id commodi at incidunt dolor repellat eveniet laudantium unde velit, distinctio enim quisquam omnis aliquid impedit iste odio quia modi ea? Quisquam quidem facilis magni. Repellat beatae eligendi aperiam mollitia perspiciatis, voluptate quaerat placeat eos nulla voluptates fuga consequatur minima porro nihil a unde sint sunt iste similique libero autem ut ad. Sapiente vero expedita nam necessitatibus maxime saepe totam dignissimos sint aut nesciunt laboriosam in fugiat qui repudiandae aperiam pariatur ad aliquid, labore delectus! Debitis officia fugit veritatis laudantium. Voluptatibus tempora inventore error odit blanditiis odio necessitatibus corporis repellendus quae alias quas qui optio, consequatur beatae dolore maiores voluptates ad iusto, minus esse accusamus cupiditate numquam? Nam, adipisci quaerat expedita perferendis praesentium voluptatibus fuga nisi quos exercitationem maiores totam atque asperiores reprehenderit iusto delectus ratione deleniti possimus nostrum iste ipsum ab consectetur ea neque officia! Exercitationem qui alias, labore culpa deserunt excepturi ut? Facere, tenetur sequi natus molestiae optio, dolores beatae perspiciatis a nam officia sed. Non quo numquam odit deserunt nostrum, expedita magnam cupiditate corrupti, est vero incidunt animi nam nesciunt saepe sequi ratione dolore facilis. Optio, nisi asperiores! Incidunt quidem quam enim provident eveniet aliquid quasi! Impedit minima maiores voluptatem dolorum sed similique minus vel tempora ipsa ad corrupti harum totam, deleniti quos ea odit eum, doloribus earum aliquid aperiam. Minus nesciunt, perspiciatis delectus quia, laboriosam, amet harum enim dolorum odit quae excepturi assumenda fugit sapiente deleniti? Similique exercitationem, harum officia iure magni, autem, assumenda nobis velit corporis maiores necessitatibus vero ad ducimus id! Labore, dolores in similique eveniet officia voluptatem repellat quaerat ullam doloremque illo. Ad, nihil hic! Itaque ipsam, amet non reprehenderit vitae alias voluptas voluptatem molestiae porro nisi recusandae modi ea perferendis omnis dolor aut et quae dignissimos mollitia minus unde ab quibusdam. Aliquam corporis praesentium aliquid nulla dolores dolor, consequuntur consectetur, necessitatibus mollitia assumenda animi debitis atque inventore unde hic. Quis culpa voluptatem, quasi perferendis ut iste optio nemo minima ad hic deleniti vitae velit sit nulla a, ullam, consequatur officia eveniet veniam! Sequi aspernatur saepe hic laborum optio dolorem eveniet quasi deleniti soluta repellendus.</p>
            </section>
        </article>
        <aside class="intersection">
            <div class="intersection__list">
                <a
                    v-for="(header, index) in headers"
                    :key="header"
                    :href="`#${index}`"
                    class="intersection__link"
                    :class="{ active: index == currentSection }"
                >
                    {{ header }}
                </a>
            </div>
        </aside>
    </main>
</template>

<style>
html {
    scroll-behavior: smooth;
}

#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
}

main {
    display: flex;
}

article {
    box-sizing: border-box;
    padding: 0 5em;
    width: 75%;
    margin-bottom: 500px;
}

.intersection {
    width: 25%;
}

.intersection__list {
    position: sticky;
    top: 20px;
    padding-left: 2em;
}

.intersection__link {
    display: block;
    padding: 2px 0 5px 2em;
    color: #2c3e50;
    text-decoration: none;
    border-left: 1px solid #ccc;
}

.intersection__link.active {
    font-weight: bold;
    border-color: #000;
}
</style>
