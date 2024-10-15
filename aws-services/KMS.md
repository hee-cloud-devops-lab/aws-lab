# AWS Key Management Service(AWS KMS)

- **데이터를 암호화할 때 사용되는 암호화 Key**를 안전하게 관리하는데 목적을 둔 서비스이다.

## Key 관리 서비스

### AWS managed key

- AWS 서비스들이 KMS를 통해 Key를 서비스 받는 것으로, 내부적으로 자동으로 일어나게 되며 사용자가 직접 제어가 불가능하다.

### Customer managed key(CMK)

- 사용자가 직접 key를 생성하고 관리하는 것
- CMK에 대한 제어는 IAM을 통해 권한을 부여받아 제어 가능하다.

### Customer key stores

- AWS에서 제공하는 또다른 key 관리형 서비스인 CloudHSM을 활용한 Key 관리 형태

## 동작 방식(CMK)

![image](https://github.com/user-attachments/assets/5ba296ae-5304-4b39-84de-535f47d85bda)


1. KMS는 Customer Master Key를 생성하는데, 해당 Master Key는 데이터를 암호화 하기 위해 사용되는 Data Key를 생성하는데 사용한다.
2. Data Key는 CMK로부터 GeneratedDataKey라는 작업을 통해 생성되는데, 이 때 두 가지의 Data key가 생성된다.
    1. Plaintext data key: 데이터 암호화 시에 사용한다.
        1. 암호화 과정은 OpenSSL이나 Encryption SDK를 사용할 수 있다.
        2. 데이터 암호화 이후에는 해당 키는 사용할 필요가 없기 때문에 폐기한다.
    2. Encrypted data key
        1. 데이터를 복호화할 때 사용한다.
3. 데이터를 복호화하려면 plaintext data key가 필요한데, 이를 위해 encrypted data key를 plaintext data key로 변환한다.

## Python + KMS를 활용한 데이터 암/복호화 예제

```python
import boto3
import base64
from Crypto.Cipher import AES

BLOCK_SIZE = 32
PADDING = '|'

key_arn = '{{ KMS_ARN }}'
message = 'This is test for KMS. written by JHSong'

client = boto3.client('kms')

data_key = client.generate_data_key(
    KeyId=key_arn,
    KeySpec='AES_256'
)

pad = lambda s: s + (BLOCK_SIZE - len(s) % BLOCK_SIZE) * PADDING

plaintext_key = data_key.get('Plaintext')
encrypted_key = data_key.get('CiphertextBlob')

###### Encrypted data ######## 
encryptor = AES.new(plaintext_key)
encrypted_data = base64.b64encode(encryptor.encrypt(pad(message)))

print("########## Encrypted Data ##############")
print(encrypted_data)

###### Decrypted data ######## 
decrypted_key = client.decrypt(CiphertextBlob=encrypted_key).get('Plaintext')
decryptor = AES.new(decrypted_key)

decrypted_str = decryptor.decrypt(base64.b64decode(encrypted_data)).decode('utf-8')

print("########## Decrypted Data ##############")
print(decrypted_str.rstrip(PADDING))
출처: https://bluese05.tistory.com/71 [ㅍㅍㅋㄷ:티스토리]
```

## 참고 자료

- https://bluese05.tistory.com/71
