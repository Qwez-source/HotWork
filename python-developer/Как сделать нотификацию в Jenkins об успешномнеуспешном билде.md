### Шанс вопроса: 6%

В Jenkins можно настроить уведомления, которые будут отправляться в случае успешного или неуспешного билда. Для этого можно использовать плагин "Extended Email Notification". 

1. Установите плагин "Extended Email Notification" через меню Jenkins -> Manage Jenkins -> Plugin Manager -> Available и найдите его по названию.
2. Настройте уведомления в настройках проекта или в консоли Jenkins:
   - Перейдите к проекту, который выполняет билд.
   - В разделе "Configure" найдите раздел "Notifications".
   - Выберите "Add notification" и выберите "Email Notification".
3. Настройте параметры уведомления:
   - Установите флажок "Enable email notification".
   - В поле "Recipients" укажите адреса электронной почты, которым будут отправляться уведомления.
   - Настройте шаблон сообщения в поле "Template", где можно использовать переменные для добавления информации о билде (например, ${BUILD_STATUS}, ${JOB_NAME}, ${BUILD_NUMBER} и т.д.).
4. Чтобы отправить уведомление в случае успешного или неуспешного билда, можно использовать скрипт в Jenkinsfile:
   ```groovy
   pipeline {
       agent any
       stages {
           stage('Build') {
               steps {
                   sh 'make'
               }
           }
       }
       post {
           success {
               mail to: 'developers@example.com', subject: "Успешный билд ${JOB_NAME} #${BUILD_NUMBER}", body: "Проект ${JOB_NAME} успешно собран в версии #${BUILD_NUMBER}."
           }
           failure {
               mail to: 'developers@example.com', subject: "Неуспешный билд ${JOB_NAME} #${BUILD_NUMBER}", body: "Произошла ошибка при сборке проекта ${JOB_NAME} версии #${BUILD_NUMBER}."
           }
       }
   }
   ```
Этот пример Jenkinsfile настроен так, что в случае успешного завершения билда будет отправлено уведомление с информацией о успешном билде, а в случае неудачи — об ошибке.