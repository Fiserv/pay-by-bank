# Implementation Guide

[//]: <> (This is where you will want to do a brief overview of ConnectPay and what it does to help clients at Fiserv)
Update here

# Information on Integration
while we know you have various ways to integrate, we are here to assist you in integrating with us here at Fiserv. If you have 
[//]: <> (You will want to step through the integration process. You will need to create paths that are common for any and all merchants. Where there are differences, we will want to fork them using sub steps with ### instead of the ## for category headings. But, it will be necessary to understand the actual process first.)
# API Integration
## Step 1 - Create a Session Token

## Step 2 - AES Key and IV Generation
AES Key Generation:\
The AES Key generated must be 256-bit in order for the Fiserv systems to decrypt the requestpayload

IV Generation:\
The IV generated must be size 96-bit in order for the Fiserv systems to decrypt the request payload

### Key Generator (Example Code - Java)
```java
private static final char[] HEX_ARRAY = "0123456789abcdef".toCharArray(); 

private String randomHexString(int size) { 
    SecureRandom random = new SecureRandom(); 
    byte[] iv = new byte[count / 8]; 
    random.nextBytes(iv); 
    return bytesToHex(iv); 
} 

public static String bytesToHex(byte[] bytes) { 
    char[] hexChars = new char[bytes.length * 2]; 
    for (int j = 0; j < bytes.length; j++) { 
        int v = bytes[j] & 0xFF; 
        hexChars[j * 2] = HEX_ARRAY[v >>> 4]; 
        hexChars[j * 2 + 1] = HEX_ARRAY[v & 0x0F]; 
    } 
    return new String(hexChars); 
} 

```

## Step 3 - Encryption & Decryption Methods
### AES Specification
| Type | Value            | 
|------|------------------|
|ALGO  |AES               | 
|CIPHER| AES/GCM/NoPadding|

### AES Encryption (Example Code - Java)
```java
public class AesUtil {
    private static final String ALGO = "AES";
    private Cipher cipher = null;
    private SecretKey secretKey = null;
    private String initializationVector = null;
    private String correlationId = null;

    public static final int GCM_TAG_LENGTH_BIT = 128;
    private static final int IV_LENGTH_BYTE = 12;

    /**
    * Initialize cipher with IV and secret key
    */
    public void init(String encKey, String initializationVector, String correlationId) throws Exception {
        try {
            cipher = Cipher.getInstance(PartnerAlgo.AES_GCM_NoPadding.getValue());
        } catch (NoSuchAlgorithmException | NoSuchPaddingException e) {
            LOG.error("Exception in AesUtil.init {}", e);
            throw e;
        }
        this.secretKey = generateKey(encKey);
        this.initializationVector = initializationVector;
        this.correlationId = correlationId;
    }

    /**
    * encryption with secret key, IV and salt (IV value)
    */
    public String encrypt(String clearText, String correlationId) throws Exception {
        if (this.correlationId == null)
            this.correlationId = correlationId;
        try {
            byte[] encrypted = doFinal(Cipher.ENCRYPT_MODE, secretKey, initializationVector,
                clearText.getBytes("UTF-8"));
            byte[] IV_BYTES = hex(initializationVector);
            byte[] cipherTextWithIv = ByteBuffer.allocate(IV_BYTES.length + encrypted.length).put(IV_BYTES)
                .put(encrypted).array();
            return base64(cipherTextWithIv);
        } catch (UnsupportedEncodingException e) {
            LOG.error("Exception in AesUtil.encrypt {}", e);
            throw e;
        } catch (Exception e) {
            LOG.error("Exception in AesUtil.encrypt {}", e);
            throw e;
        }
    }

    private SecretKey generateKey(String encKey) {
        try {
            SecretKey key = new SecretKeySpec(hex(encKey), ALGO);
            return key;
        } catch (NumberFormatException | DecoderException e) {
            LOG.error("Exception in AesUtil.generateKey {}", e);
            return null;
        }
    }

    private byte[] doFinal(int encryptMode, SecretKey key, String iv, byte[] bytes) throws Exception {
        cipher.init(encryptMode, key, new GCMParameterSpec(GCM_TAG_LENGTH_BIT, hex(iv)));
        return cipher.doFinal(bytes);
    }
}
```

### AES Decryption (Example Code - Java)
```java
public class AesUtil {
    private static final String ALGO = "AES";
    private Cipher cipher = null;
    private SecretKey secretKey = null;
    private String initializationVector = null;
    private String correlationId = null;

    public static final int GCM_TAG_LENGTH_BIT = 128;
    private static final int IV_LENGTH_BYTE = 12;
    
    /**
    * Initialize cipher with IV and secret key
    */
    public void init(String encKey, String initializationVector, String correlationId) throws Exception {
        try {
            cipher = Cipher.getInstance(PartnerAlgo.AES_GCM_NoPadding.getValue());
        } catch (NoSuchAlgorithmException | NoSuchPaddingException e) {
            LOG.error("Exception in AesUtil.init {}", e);
            throw e;
        }
        this.secretKey = generateKey(encKey);
        this.initializationVector = initializationVector;
        this.correlationId = correlationId;
    }

    /**
    * Decryption with secret key, IV and salt (IV value)
    */
    public String decrypt(String ciphertext) throws Exception {
        try {
            ByteBuffer buffer = ByteBuffer.wrap(base64(ciphertext));
            byte[] iv = new byte[IV_LENGTH_BYTE];
            buffer.get(iv);
            byte[] extractedCipherText = new byte[buffer.remaining()];
            buffer.get(extractedCipherText);
            byte[] decrypted = doFinal(Cipher.DECRYPT_MODE, secretKey, initializationVector, extractedCipherText);
            return new String(decrypted, "UTF-8");
        } catch (UnsupportedEncodingException e) {
            LOG.error("Exception in AesUtil.decrypt {}", e);
            throw e;
        } catch (Exception e) {
            LOG.error("Exception in AesUtil.decrypt {}", e);
            throw e;
        }
    }

    private SecretKey generateKey(String encKey) {
        try {
            SecretKey key = new SecretKeySpec(hex(encKey), ALGO);
            return key;
        } catch (NumberFormatException | DecoderException e) {
            LOG.error("Exception in AesUtil.generateKey {}", e);
            return null;
        }
    }

    private byte[] doFinal(int encryptMode, SecretKey key, String iv, byte[] bytes) throws Exception {
        cipher.init(encryptMode, key, new GCMParameterSpec(GCM_TAG_LENGTH_BIT, hex(iv)));
        return cipher.doFinal(bytes);
    }
}

```
### RSA Specification
| Type | Value                               | 
|------|-------------------------------------|
|ALGO  |RSA                                  | 
|CIPHER|RSA/None/OAEPwithSHA512AndMGF1Padding|

### RSA Encryption (Example Code - Java)
```java
private static final String ALGORITHM = "RSA";  
public static String encrypt(byte[] publicKey, String inputData, String rsaAlgoType) throws Exception { 

    LOG.info("Start Encrypt"); 

    // Provider added for new algorithm (RSA/None/OAEPWithSHA512AndMGF1Padding) support 
    Security.addProvider(new org.bouncycastle.jce.provider.BouncyCastleProvider()); 

    X509EncodedKeySpec ks = new X509EncodedKeySpec(publicKey); 
    KeyFactory kf = KeyFactory.getInstance(ALGORITHM); 
    PublicKey key = kf.generatePublic(ks); 
    Cipher cipher = getCipher(rsaAlgoType); 
    cipher.init(Cipher.ENCRYPT_MODE, key); 
    byte[] cryptogram = cipher.doFinal(inputData.getBytes()); 
    final String encValue = new String(Base64.encodeBase64(cryptogram)); 
    return encValue; 
} 
```

### RSA Decryption (Example Code - Java)
```java
private static final String ALGORITHM = "RSA";  
public static String decrypt(byte[] privateKey, String inputData,String rsaAlgoType) throws Exception { 
    LOG.info("Start Decrypt"); 
    PrivateKey key = KeyFactory.getInstance(ALGORITHM).generatePrivate(new PKCS8EncodedKeySpec(privateKey)); 
    Cipher cipher = getCipher(rsaAlgoType); 
    cipher.init(Cipher.DECRYPT_MODE, key); 
    byte[] decryptedBytes = cipher.doFinal(Base64.decodeBase64(inputData)); 
    LOG.info("End Decrypt"); 
    return new String(decryptedBytes, "UTF-8"); 
} 
```
Request Payload:\
Component X: This compomenmt of the request payload is the AES Key encrypted using the RSA Public Key

Component Y: This component of the of the request payload is the IV encrypted using the RSA Public Key

Component Delta: This component of the request payload is the actual payload encrypted using the AES Key and IV

Example Request Payload:
```json
{
    "componentX": "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrs",
    "componentY": "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrs",
    "componentDelta": "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdef"
}
```

Response Payload:\
The response payload must be decrypted using the merchant AES Key and IV.

Example Response Payload:
```json
{
    "componentDelta": "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789=+/abcdefghijkl"
}
```
## Step 4 - Create Consumer Profile
## Step 5a - Online Bank Login
### Step 1 - Online Bank Login Establish
### Step 2 - Online Bank Login Validate
### Step 3 - Consumer Enrollment
## Step 5b - Manual Enrollment
### Step 1 - Consumer Enrollment
### Step 2 - Consumer Micro Deposit Validation
## Step 7 - ACH Transactions
## Other REST API Calls

# SDK Integration
## SDK types
### IOS
### Android
### Website
## Step 1 - Create Session Token
## Step 2 - AES Key & IV Generation
## Step 3 - Encryption & Decryption Methods
## Step 4 - Create Consumer Profile
## Step 5 - Integrate SDK
### Step 1 - Download SDK
### Step 2 - Integrate SDK into Merchant Codebase
## Step 6 - ACH Transactions

## Other? 
### Useful Artifacts to help you Integrate
[//]: <> (Need to link below to the actual files)
- [Implementation*Guide](../documentation/implementationguide.md)
- [SDK](../assets/connect-pay_spec.zip)
