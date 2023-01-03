npm install @onesignal/node-onesignal --save


import * as OneSignal from '@onesignal/node-onesignal';
import 'dotenv/config';

const ONESIGNAL_APP_ID = '574a2efb-5c44-41dc-a234-6256091276c7';
/*
 * CREATING ONESIGNAL KEY TOKENS
 */
 const app_key_provider = {
     getToken() {
         return 'ZGVkZjU2YzMtYWM4ZS00MWQ4LWIyNGItZmJjZWVhMzI4ZGVk';
     }
 };
console.log('app_key_provider', app_key_provider.getToken());
 /**
  * CREATING ONESIGNAL CLIENT
  */
const configuration = OneSignal.createConfiguration({
    authMethods: {
        app_key: {
            tokenProvider: app_key_provider
        }
    }
});
const client = new OneSignal.DefaultApi(configuration);

/**
 * CREATE NOTIFICATION
 */
const notification = new OneSignal.Notification();
notification.app_id = ONESIGNAL_APP_ID;
notification.included_segments = ['Subscribed Users'];
notification.contents = {
  en: "Hello rohit!"
};

const {id} = await client.createNotification(notification);
console.log(id, 'id',"Notification created successfully");


/**
 * VIEW NOTIFICATION  
 */
const response = await client.getNotification(ONESIGNAL_APP_ID, id);
console.log(response , 'response');
