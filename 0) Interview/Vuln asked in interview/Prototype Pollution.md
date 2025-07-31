What is Prototype Pollution?
Prototype pollution is a vulnerability that allows an attacker to inject properties into the Object.prototype, which is the base blueprint for all JavaScript objects. This can modify the behavior of every object in a web application.
Example Payloads
 * Simple Injection: {"__proto__": {"isAdmin": true}}
   * This payload directly adds an isAdmin property to the base object prototype, potentially granting a user admin privileges.
 * Nested Injection: {"user": {"__proto__": {"isAdmin": true}}}
   * This payload works when the application is designed to handle nested objects, allowing the attacker to still reach and modify the __proto__.
 * Overwriting Properties: {"__proto__": {"isSafe": false}}
   * An attacker can overwrite an existing property like isSafe to bypass security checks.
 * Remote Code Execution (RCE):
   * Some libraries, like Lodash, use properties from the prototype for configuration. An attacker can inject a payload that changes a configuration property to execute malicious code.
   * Example: {"__proto__": {"templateSettings": {"imports": {"_": {"run": "require('child_process').execSync('malicious-command')}}}}}
Mitigation
 * Blocklist Keys: Prevent keys like __proto__ and constructor from being used in any object-merging or deserialization functions.
 * Sanitize Input: Always validate and sanitize user-provided data before using it to create or modify objects.
 * Use Object.create(null): When creating an object from user input, use Object.create(null) to ensure the object has no prototype, making it immune to pollution attacks.
