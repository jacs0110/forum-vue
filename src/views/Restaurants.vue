<template>
  <div class="container py-5">
    <NavTabs />
    <!-- 餐廳類別標籤 RestaurantsNavPills -->
    <RestaurantsNavPills 
        :categories="categories"/>

    <div class="row">
      <!-- 餐廳卡片 RestaurantCard-->
      <RestaurantCard 
        v-for="restaurant in restaurants"
        :key="restaurant.id"
        :initial-restaurant="restaurant"/>
    </div>

    <!-- 分頁標籤 RestaurantPagination -->
  </div>
</template>

<script>
import NavTabs from "./../components/NavTabs";
import RestaurantCard from "./../components/RestaurantCard";
import RestaurantsNavPills from "./../components/RestaurantsNavPills"

const dummyData ={
  restaurants: [
      {
          "id": 103,
          "name": "Breana Predoviccccc",
          "tel": "387-916-7501 x7455",
          "address": "46021 Edyth Passage",
          "opening_hours": "08:00",
          "description": "Repudiandae velit minima repudiandae dignissimos sunt nesciunt itaque totam ea.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 5,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-09-04T02:21:04.000Z",
          "CategoryId": 2,
          "Category": {
              "id": 2,
              "name": "日本料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 104,
          "name": "Micah Lubowitz",
          "tel": "593.321.5257",
          "address": "698 Mathias Tunnel",
          "opening_hours": "08:00",
          "description": "Est quasi quae at quo.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 8,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-09-03T16:44:05.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 105,
          "name": "Jocelyn Gutmann",
          "tel": "045.747.4402 x0509",
          "address": "6626 Torphy Row",
          "opening_hours": "08:00",
          "description": "Odio quo ea molestias minima minima voluptatem eveniet non laudantium.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 9,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-09-03T14:24:52.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 106,
          "name": "Salvatore Hudson",
          "tel": "(851) 948-1652 x6163",
          "address": "6888 Nicolas Ford",
          "opening_hours": "08:00",
          "description": "Eos modi eveniet vel sed quo ex quisquam. Ex repellat aut autem voluptas nostrum accusamus voluptatem. Deleniti unde nam saepe est dolores nulla.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 1,
          "Category": {
              "id": 1,
              "name": "中式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 107,
          "name": "Miracle Tillman",
          "tel": "1-639-143-0745",
          "address": "95584 VonRueden Forest",
          "opening_hours": "08:00",
          "description": "corporis dolores aliquid",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 108,
          "name": "Garth Pfannerstill",
          "tel": "736.088.2034 x84588",
          "address": "085 Adam Isle",
          "opening_hours": "08:00",
          "description": "Ut maiores possimus est aspernatur.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 3,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-09-02T18:38:29.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 109,
          "name": "Mrs. Eric Schoen",
          "tel": "(966) 081-2918",
          "address": "9094 Kessler Plains",
          "opening_hours": "08:00",
          "description": "nemo corrupti eligendi",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 4,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-09-03T14:12:08.000Z",
          "CategoryId": 3,
          "Category": {
              "id": 3,
              "name": "義大利料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 110,
          "name": "Flossie Schowalter",
          "tel": "(361) 617-4730 x447",
          "address": "544 Pacocha Divide",
          "opening_hours": "08:00",
          "description": "Perferendis deleniti aut aut fugiat architecto vero. Vitae aut quia odit ducimus autem omnis distinctio at suscipit.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 3,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-09-03T14:17:08.000Z",
          "CategoryId": 3,
          "Category": {
              "id": 3,
              "name": "義大利料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 111,
          "name": "Nico Romaguera",
          "tel": "662-690-4568 x1275",
          "address": "37964 Kyler Fields",
          "opening_hours": "08:00",
          "description": "Aut et autem earum voluptas dolor autem non nemo. Non iure eum et a repudiandae unde. Qui dolorem fuga nulla.\n \rDeserunt ea quaerat aspernatur. Corporis id voluptatem. Mollitia reprehenderit minima mollitia ipsam quibusdam molestias laudantium earum. Est eos veniam eveniet. Eum mollitia doloremque quo velit quia.\n \rSaepe eum repudiandae assumenda sunt nisi. Voluptatem quo animi aliquid numquam sed adipisci. Asperiores quo consequuntur neque maxime voluptatum iure vel natus nihil. Eaque nostrum ipsa suscipit. Sed ut minus assumenda sint ipsa voluptatem.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 3,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-09-03T14:20:30.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 112,
          "name": "Warren Kuhic",
          "tel": "251-278-9191 x0825",
          "address": "7190 Lazaro Lodge",
          "opening_hours": "08:00",
          "description": "Labore quae et dolor. Voluptas aut fugit. Tempore aliquid accusantium at repudiandae et.\n \rQuo sunt provident aliquam dignissimos debitis qui exercitationem ducimus. Eos praesentium aut quisquam et eos et voluptates odit. Vel praesentium laudantium.\n \rVoluptas sapiente dicta quis blanditiis ut. Dolorem officia temporibus rem culpa eius. Aut tempore animi provident voluptatum non voluptatibus eum optio. Minima sint eius atque eos nulla ipsam. Est voluptatum molestiae. Soluta est tempora ut et consequatur iste possimus.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 3,
          "Category": {
              "id": 3,
              "name": "義大利料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 113,
          "name": "Verner Howe",
          "tel": "(812) 346-6400 x6316",
          "address": "37851 Cormier Cliff",
          "opening_hours": "08:00",
          "description": "Deserunt quidem voluptate quaerat. Et et amet autem. Iusto sed delectus accusantium. Fugit veritatis assumenda sequi omnis sequi illum qui accusantium.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 5,
          "Category": {
              "id": 5,
              "name": "素食料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 114,
          "name": "Hazle Nitzsche",
          "tel": "1-393-411-3300 x023",
          "address": "0535 Abbott Cliffs",
          "opening_hours": "08:00",
          "description": "soluta",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 5,
          "Category": {
              "id": 5,
              "name": "素食料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 115,
          "name": "Junius Koch",
          "tel": "1-198-240-7089",
          "address": "8550 Dorothy Square",
          "opening_hours": "08:00",
          "description": "Quibusdam provident blanditiis officiis corrupti vel sit sint error. Ab exercitationem cumque ex similique asperiores est quasi tenetur asperiores. Alias dicta iusto natus et aspernatur ex nostrum. Molestias voluptatum non et nesciunt sit nemo id et.\n \rDeserunt rerum et ipsam. Enim nisi facilis a ducimus. Aut ipsa et. Quia dolorum qui. In accusamus quia nostrum maiores omnis a a neque.\n \rRepellat adipisci aspernatur. Voluptatibus sequi aut quia recusandae repudiandae. Quia quis repellat autem similique dolores.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 5,
          "Category": {
              "id": 5,
              "name": "素食料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 116,
          "name": "Emely Lueilwitz",
          "tel": "1-404-689-5222 x961",
          "address": "6399 Mckenzie Fields",
          "opening_hours": "08:00",
          "description": "eum",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 117,
          "name": "Mr. Susanna Rowe",
          "tel": "1-786-633-2743 x4691",
          "address": "23385 Leuschke Walks",
          "opening_hours": "08:00",
          "description": "exercitationem provident adipisci",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 5,
          "Category": {
              "id": 5,
              "name": "素食料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 118,
          "name": "Mayra Koss",
          "tel": "1-939-856-3697",
          "address": "07457 Gottlieb Rapid",
          "opening_hours": "08:00",
          "description": "expedita",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 119,
          "name": "Cordie Morissette",
          "tel": "861-325-0817",
          "address": "2950 Nader Oval",
          "opening_hours": "08:00",
          "description": "Corrupti amet consequatur et. Voluptates omnis architecto ad ut. Ea molestiae velit in harum. Deserunt quam qui voluptatibus sint id molestiae quidem et eaque. Odit dolores quis qui libero quia eos optio consequatur. Aut aut laborum repudiandae est aut magni velit laudantium itaque.\n \rOmnis sunt eum voluptate maxime laboriosam dolor dolores aut. Porro earum aliquam vero molestiae dolorum commodi deserunt et officia. Saepe voluptate soluta nihil at incidunt.\n \rQui ut reprehenderit ut omnis ab et ratione itaque id. Officia et voluptas iusto corrupti in eos ex. Delectus dolores error possimus dolore qui est dolorem quam. Similique dicta vel ullam nam tempore. Quis dolore quidem tempora voluptate. Molestias eius et animi officiis ab reiciendis.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 120,
          "name": "Lempi Braun",
          "tel": "683-288-8526",
          "address": "72915 Hills Meadows",
          "opening_hours": "08:00",
          "description": "Voluptas aperiam ipsum aut quis maxime. Ut animi ratione sed dolores modi voluptas veritatis. Vero est tempore commodi nisi. Impedit voluptatem eaque molestiae. Quia quia nulla dignissimos. Tempora magnam consequatur voluptatem pariatur illo eligendi enim sit.\n \rAsperiores error fugiat voluptas maxime hic. Rem ea et exercitationem dolores et. Necessitatibus deserunt magni necessitatibus nisi quidem dolores. Error sit et aperiam.\n \rA debitis voluptatum quo expedita. Voluptatibus omnis deserunt pariatur. Aut cum rerum et. Odit quisquam et necessitatibus autem soluta iste.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 5,
          "Category": {
              "id": 5,
              "name": "素食料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 121,
          "name": "Richard Hermann",
          "tel": "059.349.2429 x3294",
          "address": "02863 Krajcik Avenue",
          "opening_hours": "08:00",
          "description": "libero ea quo",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 5,
          "Category": {
              "id": 5,
              "name": "素食料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 122,
          "name": "Forrest Ryan",
          "tel": "250-328-9870 x7209",
          "address": "7659 George Dam",
          "opening_hours": "08:00",
          "description": "Quia harum asperiores.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 2,
          "Category": {
              "id": 2,
              "name": "日本料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 123,
          "name": "Hermann Cartwright",
          "tel": "938.984.6406 x42003",
          "address": "91471 Steuber Mountains",
          "opening_hours": "08:00",
          "description": "Delectus accusamus vero recusandae.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 6,
          "Category": {
              "id": 6,
              "name": "美式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 124,
          "name": "Tatum Jerde",
          "tel": "1-108-449-6047",
          "address": "1133 Alessandra Mills",
          "opening_hours": "08:00",
          "description": "dolorem at et",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 3,
          "Category": {
              "id": 3,
              "name": "義大利料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 125,
          "name": "Kyla Greenholt",
          "tel": "995.944.6062",
          "address": "241 Ebert Lodge",
          "opening_hours": "08:00",
          "description": "Nobis debitis ipsam ex nesciunt inventore et suscipit praesentium. Voluptas debitis quia veniam animi. Dignissimos est non sed recusandae quae.\n \rEnim autem vel laboriosam officia quae sunt eos. Alias voluptate vel quibusdam omnis molestiae recusandae provident non. Explicabo mollitia eius voluptas qui similique. Aut sed illum eos quo fuga eos ea vitae dolore.\n \rQui reiciendis repellendus sapiente. Velit sapiente error consectetur eaque aut sapiente sit impedit optio. Beatae a sunt blanditiis ex dolorum. In quaerat unde blanditiis. Iste dicta libero. Architecto provident sunt.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 2,
          "Category": {
              "id": 2,
              "name": "日本料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 126,
          "name": "Litzy Armstrong",
          "tel": "(639) 313-8742",
          "address": "18314 Macey Junction",
          "opening_hours": "08:00",
          "description": "Placeat hic non esse quibusdam.\nOptio at quisquam aut reprehenderit asperiores cum iste.\nDeleniti cumque et ab esse est fugit repellat.\nNam qui et nulla qui.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 2,
          "Category": {
              "id": 2,
              "name": "日本料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 127,
          "name": "Bobbie Rosenbaum",
          "tel": "470.633.8799",
          "address": "48020 Prosacco Forges",
          "opening_hours": "08:00",
          "description": "Sit nihil repellat cumque quam sunt rerum. Atque maiores recusandae exercitationem exercitationem aliquid suscipit ad rem veritatis. Velit harum ea nihil quasi. Laborum quibusdam quasi aspernatur. Soluta excepturi ipsa.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 5,
          "Category": {
              "id": 5,
              "name": "素食料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 128,
          "name": "Tyshawn Shields",
          "tel": "937.679.9239 x49120",
          "address": "9847 Bert Viaduct",
          "opening_hours": "08:00",
          "description": "Doloribus et aut beatae officia voluptatem et ipsam voluptatem eos. Ipsam sapiente a sint. Non tempore iure nisi nulla quaerat molestias harum totam. Sunt quia iure.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 129,
          "name": "Maurice Windler",
          "tel": "382.614.3303",
          "address": "87760 Juliet Summit",
          "opening_hours": "08:00",
          "description": "Non sint eum quia voluptatem. Molestiae quo nesciunt nesciunt fugiat rerum consequatur ipsum. Veritatis nihil eos nisi minima magnam. Aut dolore error deleniti praesentium quisquam facere delectus. Nihil nihil ex sit autem. Similique nihil porro vero molestiae rerum nihil consequuntur nobis itaque.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 1,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T16:42:01.000Z",
          "CategoryId": 5,
          "Category": {
              "id": 5,
              "name": "素食料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 130,
          "name": "Jocelyn O'Conner",
          "tel": "(073) 066-6108",
          "address": "427 MacGyver Cove",
          "opening_hours": "08:00",
          "description": "Eius id asperiores et.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 2,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T16:42:12.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 131,
          "name": "Sydnee Bode",
          "tel": "380.359.6700 x5755",
          "address": "44556 Erdman Meadow",
          "opening_hours": "08:00",
          "description": "Et dolores tempora aliquid inventore natus modi dolor sit.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 6,
          "Category": {
              "id": 6,
              "name": "美式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 132,
          "name": "Savion Kuvalis",
          "tel": "529.739.1625",
          "address": "45101 Smitham Estates",
          "opening_hours": "08:00",
          "description": "in quasi incidunt",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 133,
          "name": "Adriana Renner",
          "tel": "555.948.6907 x5015",
          "address": "90792 Chauncey Dam",
          "opening_hours": "08:00",
          "description": "est consequatur similique",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 134,
          "name": "Mariela Bode",
          "tel": "126-988-0759",
          "address": "770 Landen Plains",
          "opening_hours": "08:00",
          "description": "Dolorem possimus non suscipit. Voluptatem vitae tenetur facilis repellendus id fugiat rerum.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 3,
          "Category": {
              "id": 3,
              "name": "義大利料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 135,
          "name": "Landen Friesen",
          "tel": "989-115-6549",
          "address": "5666 Lueilwitz Creek",
          "opening_hours": "08:00",
          "description": "sed ea aliquid",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 2,
          "Category": {
              "id": 2,
              "name": "日本料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 136,
          "name": "Geo Dooley",
          "tel": "239-387-5034 x355",
          "address": "455 Julia Field",
          "opening_hours": "08:00",
          "description": "qui esse enim",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 137,
          "name": "Deanna Pagac",
          "tel": "088.627.1761 x73660",
          "address": "21610 Jo Fork",
          "opening_hours": "08:00",
          "description": "Molestias commodi at delectus quia exercitationem deserunt sapiente error dicta. Ducimus atque illo modi officia dolorem. Est modi minima beatae.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 1,
          "Category": {
              "id": 1,
              "name": "中式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 138,
          "name": "Zachariah Larson",
          "tel": "1-398-793-6978 x32863",
          "address": "025 Sofia Hills",
          "opening_hours": "08:00",
          "description": "Ad dolorem eius aut totam assumenda vitae amet unde.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 5,
          "Category": {
              "id": 5,
              "name": "素食料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 139,
          "name": "Bernardo Schuppe",
          "tel": "671.085.2262",
          "address": "3816 Fred Brook",
          "opening_hours": "08:00",
          "description": "Fugiat laudantium aut optio.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 140,
          "name": "Alford Robel",
          "tel": "988.851.7961 x7089",
          "address": "159 Ziemann Glens",
          "opening_hours": "08:00",
          "description": "Possimus recusandae aspernatur vitae. Qui illo et consectetur. Aut ipsa et incidunt.\n \rMinus illo quia sapiente rerum delectus laborum unde sed. Animi magni aut laborum sint. Corrupti omnis inventore deleniti nulla totam quia delectus. Temporibus odit rerum praesentium. Quaerat atque voluptas quod et aut mollitia.\n \rRatione repellat inventore ea enim. Odit vero eum iusto mollitia autem iusto eos minima. Est ad culpa eum et et eum nisi. Nisi aut eius iure et consequatur officia et.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 141,
          "name": "Norma Daugherty",
          "tel": "1-111-630-7266",
          "address": "46884 Glennie Island",
          "opening_hours": "08:00",
          "description": "aut",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 6,
          "Category": {
              "id": 6,
              "name": "美式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 142,
          "name": "Hortense Cummerata",
          "tel": "122.349.6352",
          "address": "60642 Ledner Curve",
          "opening_hours": "08:00",
          "description": "Perferendis a excepturi molestiae recusandae itaque deserunt omnis quia. Vero ea consequatur dolorum. Velit earum voluptas iste consequuntur et ipsum modi. Voluptatem sint velit molestiae iure qui non vitae facere.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 3,
          "Category": {
              "id": 3,
              "name": "義大利料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 143,
          "name": "Dameon O'Kon V",
          "tel": "543.687.3029",
          "address": "70474 Lexie Key",
          "opening_hours": "08:00",
          "description": "Est corporis quibusdam ipsum qui sint. Voluptates consequatur facere. Sapiente et et ducimus et ad itaque pariatur consequatur et. Voluptatum voluptatem totam qui omnis voluptatem magnam. Quia aut quia fugit aut officiis.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 2,
          "Category": {
              "id": 2,
              "name": "日本料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 144,
          "name": "Ellis Crist",
          "tel": "1-705-670-1956 x995",
          "address": "328 Legros Harbor",
          "opening_hours": "08:00",
          "description": "Voluptas magni atque.\nExcepturi et iste nesciunt eaque est.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 1,
          "Category": {
              "id": 1,
              "name": "中式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 145,
          "name": "Miss Clinton Marquardt",
          "tel": "(512) 091-5707 x566",
          "address": "665 Kiehn Courts",
          "opening_hours": "08:00",
          "description": "eos labore at",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 146,
          "name": "Ms. Cleta Koepp",
          "tel": "474.686.9647",
          "address": "96573 Mayra Street",
          "opening_hours": "08:00",
          "description": "molestias quia non",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 147,
          "name": "Ila Runolfsson",
          "tel": "271-102-5660 x399",
          "address": "19267 Cremin Flat",
          "opening_hours": "08:00",
          "description": "Numquam nesciunt id illum culpa. Possimus doloremque quod aut deserunt. Esse nulla esse sed totam temporibus eum ut. Asperiores repudiandae ipsam possimus.",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 148,
          "name": "Mr. Caleigh Jaskolski",
          "tel": "387.732.0773",
          "address": "53761 Hansen Squares",
          "opening_hours": "08:00",
          "description": "quisquam id reprehenderit",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 1,
          "Category": {
              "id": 1,
              "name": "中式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 149,
          "name": "Amber Welch",
          "tel": "1-266-226-7357",
          "address": "48624 Berge Fort",
          "opening_hours": "08:00",
          "description": "fugiat sunt non",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 6,
          "Category": {
              "id": 6,
              "name": "美式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 150,
          "name": "Natalie Greenfelder",
          "tel": "(571) 207-0708",
          "address": "82082 Camron Gardens",
          "opening_hours": "08:00",
          "description": "commodi",
          "image": "http://lorempixel.com/640/480/food",
          "viewCount": 0,
          "createdAt": "2019-08-30T10:04:58.000Z",
          "updatedAt": "2019-08-30T10:04:58.000Z",
          "CategoryId": 7,
          "Category": {
              "id": 7,
              "name": "複合式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 151,
          "name": "Add from api (new)",
          "tel": "00000000",
          "address": "00000000",
          "opening_hours": "13:00",
          "description": "86888",
          "image": "https://i.imgur.com/dSgocEs.png",
          "viewCount": null,
          "createdAt": "2019-09-02T13:29:17.000Z",
          "updatedAt": "2019-09-02T13:57:37.000Z",
          "CategoryId": 6,
          "Category": {
              "id": 6,
              "name": "美式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 152,
          "name": "Post from Local",
          "tel": "",
          "address": "",
          "opening_hours": "",
          "description": "",
          "image": null,
          "viewCount": null,
          "createdAt": "2019-09-02T13:46:29.000Z",
          "updatedAt": "2019-09-02T13:56:03.000Z",
          "CategoryId": 4,
          "Category": {
              "id": 4,
              "name": "墨西哥料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      },
      {
          "id": 153,
          "name": "Post from Local (4)",
          "tel": "",
          "address": "",
          "opening_hours": "",
          "description": "",
          "image": "https://i.imgur.com/vWzxdkE.png",
          "viewCount": null,
          "createdAt": "2019-09-02T13:48:13.000Z",
          "updatedAt": "2019-09-02T18:38:25.000Z",
          "CategoryId": 6,
          "Category": {
              "id": 6,
              "name": "美式料理",
              "createdAt": "2019-08-30T10:04:58.000Z",
              "updatedAt": "2019-08-30T10:04:58.000Z"
          }
      }
  ],
  categories: [
    {
        "id": 1,
        "name": "中式料理",
        "createdAt": "2019-08-30T10:04:58.000Z",
        "updatedAt": "2019-08-30T10:04:58.000Z"
    },
    {
        "id": 2,
        "name": "日本料理",
        "createdAt": "2019-08-30T10:04:58.000Z",
        "updatedAt": "2019-08-30T10:04:58.000Z"
    },
    {
        "id": 3,
        "name": "義大利料理",
        "createdAt": "2019-08-30T10:04:58.000Z",
        "updatedAt": "2019-08-30T10:04:58.000Z"
    },
    {
        "id": 4,
        "name": "墨西哥料理",
        "createdAt": "2019-08-30T10:04:58.000Z",
        "updatedAt": "2019-08-30T10:04:58.000Z"
    },
    {
        "id": 5,
        "name": "素食料理",
        "createdAt": "2019-08-30T10:04:58.000Z",
        "updatedAt": "2019-08-30T10:04:58.000Z"
    },
    {
        "id": 6,
        "name": "美式料理",
        "createdAt": "2019-08-30T10:04:58.000Z",
        "updatedAt": "2019-08-30T10:04:58.000Z"
    },
    {
        "id": 7,
        "name": "複合式料理",
        "createdAt": "2019-08-30T10:04:58.000Z",
        "updatedAt": "2019-08-30T10:04:58.000Z"
    },
    {
        "id": 12,
        "name": "非常厲害料理",
        "createdAt": "2019-09-02T14:05:45.000Z",
        "updatedAt": "2019-09-02T14:05:45.000Z"
    },
    {
        "id": 14,
        "name": "超級厲害料理",
        "createdAt": "2019-09-02T14:12:27.000Z",
        "updatedAt": "2019-09-02T14:12:27.000Z"
    }
  ],
  page: 1,
  totalPage: [1, 2, 3, 4, 5],
  prev: 1,
  next: 2,
  categoryId: ''
}

export default {
  components: {
    NavTabs,
    RestaurantCard,
    RestaurantsNavPills
  },
  data () {
    return {
      categories: [],
      categoryId: -1,
      currentPage: 1,
      restaurants: [],
      totalPage: -1
    }
  },
  created(){
    this.fetchRestaurants()
  },
  methods: {
    fetchRestaurants () {
      this.categories = dummyData.categories
      this.categoryId = dummyData.categoryId
      this.currentPage = dummyData.page
      this.restaurants = dummyData.restaurants
      this.totalPage = dummyData.totalPage.length
    }
  }

};
</script>