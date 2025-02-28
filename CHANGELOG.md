# Change Log

All notable changes to this project will be documented in this file.
See [Conventional Commits](https://conventionalcommits.org) for commit guidelines.

## [0.2.1](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.2.0...v0.2.1) (2023-01-19)

**Note:** Version bump only for package aws-proton-plugins-for-backstage





# [0.2.0](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.1.7...v0.2.0) (2022-12-20)

### Features

- Support using Proton across multiple AWS accounts in one Backstage app ([8c8778a](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/8c8778aa8ab9cc7c9c996482e323b30d50326753))

### BREAKING CHANGES

You must make two changes to your Backstage app source code when upgrading your Backstage app to use this version of the Proton plugins:

1. Pass configuration to the Proton backend plugin router:
```diff
diff --git a/packages/backend/src/plugins/awsProton.ts b/packages/backend/src/plugins/awsProton.ts
index 68968b9..37de05a 100644
--- a/packages/backend/src/plugins/awsProton.ts
+++ b/packages/backend/src/plugins/awsProton.ts
@@ -4,5 +4,6 @@ import { PluginEnvironment } from '../types';
 export default async function createPlugin(env: PluginEnvironment) {
   return await createRouter({
     logger: env.logger,
+    config: env.config,
   });
 }
```

2. Pass configuration to the Proton scaffolder action:
```diff
diff --git a/packages/backend/src/plugins/scaffolder.ts b/packages/backend/src/plugins/scaffolder.ts
index d566691..fdb0f42 100644
--- a/packages/backend/src/plugins/scaffolder.ts
+++ b/packages/backend/src/plugins/scaffolder.ts
@@ -22,7 +22,7 @@ export default async function createPlugin(
     config: env.config,
   });

-  const actions = [...builtInActions, createAwsProtonServiceAction()];
+  const actions = [...builtInActions, createAwsProtonServiceAction({ config: env.config })];

   return await createRouter({
     logger: env.logger,
```

## [0.1.7](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.1.6...v0.1.7) (2022-12-05)

**Note:** Version bump only for package aws-proton-plugins-for-backstage

## [0.1.6](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.1.5...v0.1.6) (2022-11-14)

### Bug Fixes

- run prettier to get consistent code style ([b167e29](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/b167e29abd1b5fd51145bed8ae651a4c750f9654))

## [0.1.5](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.1.4...v0.1.5) (2022-11-11)

**Note:** Version bump only for package aws-proton-plugins-for-backstage

## [0.1.4](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.1.3...v0.1.4) (2022-11-09)

### Bug Fixes

- Support scaffolding pipeline-less services ([9655f82](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/9655f822182a6184712ff76e7f2075a0b46bc559))

## [0.1.3](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.1.2...v0.1.3) (2022-07-19)

**Note:** Version bump only for package aws-proton-plugins-for-backstage

## [0.1.2](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.1.1...v0.1.2) (2022-06-21)

**Note:** Version bump only for package aws-proton-plugins-for-backstage

## [0.1.1](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.1.0...v0.1.1) (2022-06-21)

**Note:** Version bump only for package aws-proton-plugins-for-backstage

# [0.1.0](https://github.com/awslabs/aws-proton-plugins-for-backstage/compare/v0.0.0...v0.1.0) (2022-06-20)

### Bug Fixes

- add user agent to proton calls ([b02903a](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/b02903a0be4ec90e083d98e7fb2805f88239b823))
- Fill in Proton console URL link ([edd5280](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/edd5280e4752fa7f4c9324eb214358dfa87980a0))
- Move around content on the entity card, add more test fixtures ([4806b41](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/4806b411104a8b0e3a382c8ea6a01bdfa630ab49))
- support EKS service account creds ([f9f2e22](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/f9f2e22646c9e0c00df4c9a3a6c99672a7f080c5))

### Features

- Change the annotation to aws.amazon.com ([8fad850](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/8fad85099d2b0f3d8f4baf74b764cb295e4c9b18))
- change the plugin names to the AWS namespace ([7ca8aeb](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/7ca8aeb9e6820cb2508b8cb067b177e8acfc1e5c))

### Reverts

- Revert "Bump yn from 4.0.0 to 5.0.0 in /plugins/aws-proton-backend" ([623c411](https://github.com/awslabs/aws-proton-plugins-for-backstage/commit/623c411911d6635a451b91eed1a9e8dbf6464ed8))

## 0.0.0 (2022-04-04)

Initial release
