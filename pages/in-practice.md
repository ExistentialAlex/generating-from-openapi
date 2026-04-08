---
---

# In Practice

<div class="grid grid-cols-2 gap-4">
<div>
    <p v-click="1">It turns this:</p>
    <div v-click="1">
```json [openapi.json] {all}{maxHeight:'350px'}
{
  "openapi": "3.1.0",
  "info": {
    "title": "orval-test API",
    "description": "API Documentation for the orval-test.",
    "version": "0.0.0"
  },
  "paths": {
    "/auth/login": {
      "post": {
        "operationId": "postAuthLogin",
        "requestBody": {
          "content": {
            "application/json": {
              "schema": {
                "type": "object",
                "properties": {
                  "email": {
                    "type": "string"
                  },
                  "organisation": {
                    "type": "string"
                  }
                },
                "required": [
                  "email",
                  "organisation"
                ]
              }
            }
          }
        },
        "description": "Login to the BFF.",
        "tags": [
          "authentication"
        ],
        "responses": {
          "200": {
            "description": "Login Successful",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "message": {
                      "type": "string"
                    }
                  },
                  "required": [
                    "message"
                  ]
                }
              }
            }
          },
          "401": {
            "description": "Login not authorized",
            "content": {
              "application/json": {
                "schema": {
                  "type": "object",
                  "properties": {
                    "message": {
                      "type": "string"
                    }
                  },
                  "required": [
                    "message"
                  ]
                }
              }
            }
          }
        }
      }
    }
  }
}
```
    </div>
    </div>
  
  <div>
    <p v-click="2">Into this:</p>
    <div v-click="2">

```ts [api/authentication.ts] {all}{maxHeight:'350px'}
import type {
  PostAuthLogin200,
  PostAuthLogin401,
  PostAuthLoginBody
} from '../../models';

/**
* Login to the BFF.
*/
export type postAuthLoginResponse200 = {
  data: PostAuthLogin200
  status: 200
}

export type postAuthLoginResponse401 = {
  data: PostAuthLogin401
  status: 401
}

export type postAuthLoginResponseSuccess = (postAuthLoginResponse200) & {
  headers: Headers;
};
export type postAuthLoginResponseError = (postAuthLoginResponse401) & {
  headers: Headers;
};

export type postAuthLoginResponse = (postAuthLoginResponseSuccess | postAuthLoginResponseError)

export const getPostAuthLoginUrl = () => {
  return `/auth/login`
}

export const postAuthLogin = async (postAuthLoginBody: PostAuthLoginBody, options?: RequestInit): Promise<postAuthLoginResponse> => {
  
  const res = await fetch(getPostAuthLoginUrl(),
    {      
      ...options,
      method: 'POST',
      headers: { 'Content-Type': 'application/json', ...options?.headers },
      body: JSON.stringify(
        postAuthLoginBody,)
    }
  )

  const body = [204, 205, 304].includes(res.status) ? null : await res.text();
  
  const data: postAuthLoginResponse['data'] = body ? JSON.parse(body) : {}
  return { data, status: res.status, headers: res.headers } as postAuthLoginResponse
}
```
    </div>
  </div>
</div>
