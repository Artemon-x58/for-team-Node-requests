# for-team-Node-requests

BASE_URL = "https://team-project-part-node.onrender.com"

                                                                                            signup----POST

Запрос post("/api/auth/signup") передаем все данные пользователя, которые он внес при регистрации. И перенаправляем пользователя на страницу логинизации
Возращается код 201 и емеил зарегестрированного пользователя

                                                                                            signin----POST

Запрос post("/api/auth/signin") передаем емаил и пароль пользователя

Возращается код 200 и токен пользователя который залогинился, и бросаем его в локал сторедж

                                                                                            forgot-password----POST

Запрос post("/api/auth/forgot-password") передаем емеил пользователя, который забыл пароль

Возращается код 200 и сообщение "The new password was created successfully". Отправляется пистмо на почту указаную в запросе, с новым паролем. И перенаправляем пользователя на страницу логинизации

                                     КО ВСЕМ СЛЕДУЮЩИЕМ ЗАПРОСАМ ПЕРЕДАЕМ В ЗАГОЛОВКАХ ТОКЕН ПОЛЬЗОВАТЕЛЯ, КОТОРЫЙ МЫ ПОЛУЧАЕМ ПОСЛЕ ЛОГИНИЗАЦИИ





                                                                                            signout----POST

Запрос post("/api/auth/signout") токен

Возращается код 204 и сообщение "Logout success".

                                                                                            current----GET

Запрос get("/api/user/current") токен

Возращается большой объект с ключами:user, recommendedCalories, caloriesToday, recommendedWater, waterToday, recommendedFood, breakfast, lunch, dinner, snack Это всё кидаем в редакс состояние и наполняем HomePage

                                                                                            avatar----PATCH

Запрос patch("/api/user/avatars") токен

Возращается ............................

                                                                                            update----PUT

Запрос put("/api/user/update") токен и все данные настроек, не важно что пользователь поменял, нужно отдать всё

Возращается код 200 и полная обновленная информация данного пользователя

                                                                                            goal----PUT

Запрос put("/api/user/goal") токен и и новую цель пользователя, которую он указал

Возращается код 200 и полная обновленная информация данного пользователя

                                                                                            weight----POST

Запрос post("/api/user/goal") токен и и новый вес пользователя

Возращается код 201 и новый вес пользователя

                                                                                            food-intake ----POST

Запрос post("/api/user/food-intake") токен и ОБЯЗАТЕЛЬНО МАССИВ С ОБЪЕКТОМ ИЛИ ОБЪЕКТАМИ взависимости от того, сколько продуктов пользователь добавил за один раз. В каждом объекте обязательные поля:
meals(string), title(string), calories(number), carbohydrates(number), protein(number), fat(number)

Возращается код 201 и объект с обновленными массивами для каждого приему пищи

                                                                                            food-intake by ID ----PUT

Запрос put("/api/user/food-intake/:id") токен и все поля обязательны пример:{
"meals": "dinner",
"title": "cola",
"calories": 222,
"carbohydrates": 14,
"protein": 50,
"fat": 10
}

Возращается код 200 и новый обновленный объект с новым id

                                                                                            food-intake by ID ----DELETE

Запрос put("/api/user/food-intake/:id") токен и все полe {"meals": "dinner(например)"}

Возращается код 200 и сообхение "Success"

                                                                                            food-intake ----DELETE

Запрос delete("/api/user/food-intake") токен и meals т.е. завтрак, ланч, ужин или снек

Возращается код 200

                                                                                            water-intake ----POST

Запрос post("/api/user/water-intake") токен и количество воды в милилитрах

Возращается код 200 и обновленный объект с количеством воды выпитым юзером за текущую дату

                                                                                            water-intake ----DELETE

Запрос delete("/api/user/water-intake") токен

Возращается код 200 и обновленный объект с количеством воды выпитым юзером за текущую дату

                                                                                           statistics ----GET

Запрос get("/api/user/statistics") токен и {"month": "название месяца"}

Возращается объект с масивами для воды, веса и калорий по каждому дню за выбранный месяц

                                                                                           recommended-food ----GET

Запрос get("/api/recommended-food") токен

Возращается код 200 и массив объектов со всеми рекомендоваными продуктами и их описание
