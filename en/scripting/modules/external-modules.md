
It's permitted to use external modules out of project. For example, modules from NPM.

## Module system

Creator supports both ECMAScript modules and CommonJS modules.

### Determining module system

Creator Determinates the format of a module by a serials of rules.
The rules are similar to [how NodeJS determinate module format](https://nodejs.org/api/packages.html#packages_determining_module_system),
with a few exception.

The following modules are treated as ECMAScript modules, when referenced by import statements within ECMAScript module code:

- Modules within project.

- Files ending in `.mjs`.

- Files ending in `.js` when the nearest parent `package.json` file contains a top-level `"type"` field with a value of `"module"`.

In all other cases, modules are treated as CommonJS modules.

### Interoperability with CommonJS

ECMAScript modules can be interoperable with CommonJS modules,
with semantics as specified in [NodeJS](https://nodejs.org/api/esm.html#esm_interoperability_with_commonjs). Here list the key points:

- When importing a CommonJS module, it can be reliably imported using the ES module default import or its corresponding sugar syntax.

- In addition, the CommonJS named exports of every imported CommonJS module are attempted to determined to provide them as separate ES module exports using a static analysis process.
