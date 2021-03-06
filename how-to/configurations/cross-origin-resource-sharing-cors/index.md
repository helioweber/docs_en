# Cross-Origin Resource Sharing (CORS)

[Edit on GitHub <svg width="14" height="14" xmlns="http://www.w3.org/2000/svg"><g fill="none" stroke="#F3652B"><path d="M4.81.71H.672v11.43H12.1V8.001" stroke-width=".8"/><path d="M6.87.786h5.155V5.94M6.31 6.5L12.026.786"/></g></svg>](https://github.com/aziontech/docs_en/edit/master/how-to/configurations/cross-origin-resource-sharing-cors/index.md)

Cross-Origin Resource Sharing (CORS) is a mechanism for using HTTP headers to give access permission to a User Agent for specific resources that are on a different origin server to the document in use.

An example of a cross-origin request is a HTML page provided by domain “A”, which requests a CSS stylesheet, provided by domain “B”. For security reasons, most browsers prevent cross-origin HTTP requests originated by scripts.

Here are some examples of CORS configurations:

> 1. [CORS permission for all origins](#permissao-de-cors-para-todas-as-origens)
> 2. [CORS permission for specific origins](#permissao-de-cors-para-origens-determinadas)

---

## 1. CORS permission for all origins

To allow CORS within a configuration, without any restriction on the origin:

1. Go to the Content Delivery menu of [Real-Time Manager](https://manager.azion.com/).
2. Edit the required Content Delivery configuration.
3. In the Rules Engine tab, create a new rule in Response Phase. Here’s an example.

| **Name:** | CORS |
|-----------|------|
| **Criteria:** | **if** ${*uri*} **starts with** */your-uri* |
| **Behavior:** | **then** Add Response Header *Access-Control-Allow-Origin: ** |

---

## 2. CORS permission for specific origins {#permissao-de-cors-para-origens-determinadas}

To enable CORS within a configuration for some specific origin servers, you will need the  [Application Acceleration] ({% tl documentation_products_application_acceleration %}) product.

1. Go to the Content Delivery menu of [Real-Time Manager](https://manager.azion.com/).
2. Edit the required Content Delivery configuration.
3. In the Main Settings tab, start up Application Acceleration and save the setting.
4. In the Rules Engine tab, create a new rule in Response Phase. Here’s an example.

| **Name:** | CORS |
|-----------|------|
| **Criteria:** | **if** *${http_origin}* **is equal** *http://your.domain1.com*<br>**or** *${http_origin}* **is equal** *http://your.domain2.com*<br>**or** *${http_origin}* **is equal** *http://your.domain3.com* |
| Behavior: | **then** Add Response Header *Access-Control-Allow-Origin: ${http_origin}* |

---

Didn't find what you were looking for? [Open a support ticket.](https://tickets.azion.com/)   