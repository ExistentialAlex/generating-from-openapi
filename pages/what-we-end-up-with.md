---
layout: default
---

# What we end up with

<div class="grid grid-cols-3 gap-4">
<div>
    <p v-click="1">Models</p>
    <div v-click="1">
```ts [postAuthLogin200.ts] {all}
export type PostAuthLogin200 = {
  message: string;
};
```
```ts [postAuthLogin401.ts] {all}
export type PostAuthLogin401 = {
  message: string;
}
```
    </div>
  </div>
  <div>
    <p v-click="2">API Functions</p>
    <div v-click="2">
```ts [api/authentication.ts] {all}{maxHeight:'350px'}
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
  <div>
    <p v-click="3">And optionally. Mocks.</p>
    <div v-click="3">
```ts [api/authentication.msw.ts] {all}{maxHeight:'350px'}
export const getPostAuthLoginResponseMock = (overrideResponse: Partial<Extract<PostAuthLogin200, object>> = {}): PostAuthLogin200 => ({message: faker.string.alpha({length: {min: 10, max: 20}}), ...overrideResponse})

export const getPostAuthLoginMockHandler = (overrideResponse?: PostAuthLogin200 | ((info: Parameters<Parameters<typeof http.post>[1]>[0]) => Promise<PostAuthLogin200> | PostAuthLogin200), options?: RequestHandlerOptions) => {
  return http.post('*/auth/login', async (info: Parameters<Parameters<typeof http.post>[1]>[0]) => {
    return HttpResponse.json(overrideResponse !== undefined
    ? (typeof overrideResponse === "function" ? await overrideResponse(info) : overrideResponse)
    : getPostAuthLoginResponseMock(),
      { status: 200
      })
  }, options)
}
export const getAuthenticationMock = () => [
  getPostAuthLoginMockHandler()
]
```
    </div>
  </div>
</div>
