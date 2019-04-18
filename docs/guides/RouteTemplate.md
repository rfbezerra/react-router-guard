# Route Template
You can group template by feature for example you have UserLayout and MainLayout, in MainLayout you have sidebar and header is using for all sub route and in UserLayout you don't have sidebar and header, react-router-guard can solve it for you, this is example for this case

```jsx
export default [
  {
    path: '/user',
    component: dynamicWrapper(() => import('./layouts/UserLayout')), // file location on your project
    canActivate: [checkAuth],
    routes: [
      {
        path: '/user/profile',
        component: dynamicWrapper(() => import('./pages/User/Profile')),
      },
      {
        path: '/user/setting',
        component: dynamicWrapper(() => import('./pages/User/Setting')),
      },
    ],
  },
  {
    path: '/',
    component: dynamicWrapper(() => import('./layouts/MainLayout')),
    routes: [
      {
        path: '/',
        exact: true,
        component: dynamicWrapper(() => import('./pages/Home')),
      },
      {
        path: '/services',
        component: dynamicWrapper(() => import('./pages/Services')),
      },
    ],
  },
];
```