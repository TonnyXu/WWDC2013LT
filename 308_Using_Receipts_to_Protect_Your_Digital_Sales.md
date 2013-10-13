# Using Receipts to Protect Your Digital Sales

## Must know

1. **Unified receipt** format for iOS 7 & OS X
2. **96%** of the Top-grossing apps are free and use in-app-purchase
3. 2 ways of validation: on-device, server-to-server. **Do not do** device-server validation
4. Paid to Free transition is possible since iOS 7 and Mavericks
    * Bundle Version and purchase date
5. iOS 6 receipt API is deprecated
6. Use Test Env with Dev cert
    * Pitfall 1: Not using test account created from iTunesConnect
    * Pitfall 2: Product cert + Test env is possible(in review). Fail this case will get rejected

## Tech detail

1. Link `OpenSSL`(`asn1c` if necessary) as static library
    * Never use dynamic library
    * If you really want to enhance the security, do not use them, write your own
2. What's in the receipt?
    * Bundle Identifier
    * Bundle Version
    * Vendor Identifier(iOS), GUID(OS X)
    * SHA1 Hash
    * Payload
        * Quantity
        * Product id
        * Transaction id
        * Purchase date
2. 3-step validation process
    1. Validate signature
    2. Confirm device
    3. Confirm purchases 
3. Do the validation in the `main()` **before** do anything
    * iOS: YOU need to decide the UI/UX when validation failed. Don't quit app. (Do not use `abort()`)
    * OS X: System will handle
4. If possible, do server-to-server validation
5. Refresh receipt if it's not exit
    * Sign in UI is prompted via system
    * Do it only if the receipt is missing


## Test Env
1. Even support simulating Volume Purchase
2. Signed with Development certification
3. OS X **must** run *from Finder*, then exit with code 173
4. Use Test Env account

## Unclear

1. Use something special in your validation?
