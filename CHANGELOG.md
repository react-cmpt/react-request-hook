# [4.0.0](https://github.com/react-cmpt/react-request-hook/compare/v3.0.0...v4.0.0) (2021-06-02)


### Features

* **useResource:** Use cache initialization state ([#2](https://github.com/react-cmpt/react-request-hook/pull/2))
* **context:** separate the values of provider(props) ([35ea8a2](https://github.com/react-cmpt/react-request-hook/commit/35ea8a2b01affbbe17867ada2d541089b7c15277))
  ```diff
  - <RequestProvider value={axiosInstance}>
  + <RequestProvider instance={axiosInstance}>
      <App />
    </RequestProvider>,
  ```
* **type:** split with RequestContextConfig (null) ([fd91fcb](https://github.com/react-cmpt/react-request-hook/commit/fd91fcb7d7832778034c83ce965f12c58d2eaea0))
  ```tsx
  export type RequestContextConfig<T = any> = {
    instance?: AxiosInstance;
    cache?: Cache<T> | false;
    cacheKey?: CacheKeyFn<T>;
    cacheFilter?: CacheFilter<T>;
  };

  export type RequestContextValue<T = any> = RequestContextConfig<T> | null;
  ```



# [3.0.0](https://github.com/react-cmpt/react-request-hook/compare/v2.2.2...v3.0.0) (2021-01-03)


### Features

* **useRequest:** swap returns ([7169e9e](https://github.com/react-cmpt/react-request-hook/commit/7169e9e5fd1fbb4d89f1f8b729d7bb773545f1cc))
   ```tsx
   // before
   const [request, createRequest] = useRequest(...);
   // now
   const [createRequest, request] = useRequest(...);
   ```
* return other responses ([3924e0c](https://github.com/react-cmpt/react-request-hook/commit/3924e0cb67e66155702ff1ea6d113a2f69f462b5))
  ```tsx
  const [createRequest] = useRequest(...);
  
  const fetch = async () => {
    // before
    const response = await createRequest.ready();

    // now. [T, Omit<AxiosResponse<T>, "data">]
    const [response, otherAxiosReponse] = await createRequest.ready();
  }
  ```
  ```tsx
  // before
  const [{ data, error, isLoading, cancel }] = useResource(...);
  
  // now. other: Omit<AxiosResponse, "data">
  const [{ data, other, error, isLoading, cancel }] = useResource(...);
  ```



## [2.2.2](https://github.com/react-cmpt/react-request-hook/compare/v2.2.1...v2.2.2) (2020-12-27)


### Building

* To ensure compatibility in the emitted JavaScript. (`esModuleInterop`, `allowSyntheticDefault`) (for dependencies) ([b62273f](https://github.com/react-cmpt/react-request-hook/commit/b62273f4c84678a515cf0b07e6ac620a6245e852))
 

## [2.2.1](https://github.com/react-cmpt/react-request-hook/compare/v2.2.0...v2.2.1) (2020-12-25)


### Building

* Not allow Synthetic Default Imports. (for `fast-deep-equal`) ([645d2c2](https://github.com/react-cmpt/react-request-hook/commit/645d2c296421f823d98cf5a3ea302ad20d383dfd))


# [2.2.0](https://github.com/react-cmpt/react-request-hook/compare/v2.1.1...v2.2.0) (2020-12-24)


### Bug Fixes

* **useResource:** canceller closure ([f0d63ef](https://github.com/react-cmpt/react-request-hook/commit/f0d63ef332b1e5f7c215f0c01e9bb7f7a6d0a704))
* block state update on uninstall ([a7242b9](https://github.com/react-cmpt/react-request-hook/commit/a7242b9f309ea55653eb744b71d51e17716ae524))


### Features

* return original error ([eedcc72](https://github.com/react-cmpt/react-request-hook/commit/eedcc72971cd9bbf04f9550a2db58e2b110fb573))
* **useResource:** add res type and useDeepMemo ([d56da08](https://github.com/react-cmpt/react-request-hook/commit/d56da086622b0036142e3034758bf97a6bb13c06))
* **utils:** useDeepMemo ([c7af8cd](https://github.com/react-cmpt/react-request-hook/commit/c7af8cd23ae8e9c0d52a5b18d2146c529b885ef1))
* **utils:** useMountedState hook ([0596a63](https://github.com/react-cmpt/react-request-hook/commit/0596a63edd5316085807ea643b61ced566319ff1))
* **deps:** upgrade axios -> ^0.19 ([cdc899f](https://github.com/react-cmpt/react-request-hook/commit/cdc899f8db8cc4ef107fa471c15605dc17e78c85))



