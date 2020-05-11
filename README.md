[![Build status](https://travis-ci.org/jchambers/java-otp.svg?branch=master)](https://travis-ci.org/jchambers/java-otp)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.eatthepath/java-otp/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.eatthepath/java-otp)

java-otp is a Java library for generating [HOTP (RFC 4226)](https://tools.ietf.org/html/rfc4226) or [TOTP (RFC 6238)](https://tools.ietf.org/html/rfc6238) one-time passwords.

## Getting java-otp

You can download java-otp as a jar file (it has no dependencies) from the [GitHub releases page](https://github.com/jchambers/java-otp/releases) and add it to your project's classpath. If you're using Maven (or something that understands Maven dependencies) to build your project, you can add java-otp as a dependency:

```xml
<dependency>
  <groupId>com.eatthepath</groupId>
  <artifactId>java-otp</artifactId>
  <version>0.2.0</version>
</dependency>
```

java-otp works with Java 8 or newer. If you need support for versions of Java older than Java 8, you may try using [java-otp v0.1](https://github.com/jchambers/java-otp/releases/tag/java-otp-0.1.0) (although it is no longer supported).

## Usage

To demonstrate generating one-time passwords, we'll focus on the TOTP algorithm. To create a TOTP generator with a default password length (6 digits), time step (30 seconds), and HMAC algorithm (HMAC-SHA1):

```java
TimeBasedOneTimePasswordGenerator totp = new TimeBasedOneTimePasswordGenerator();

byte[] seed = Base32.decode("OTP-TOKEN-SEED");

SecretKeySpec macKey =new SecretKeySpec(seed, totp.getAlgorithm());

Instant now = Instant.now();

System.out.format("Current password: %06d\n", totp.generateOneTimePassword(macKey, now));
```

## Validation tool

https://totp.app/

1、Input `otp_token` to Secret Key

2、Application Name fill in any string

3、Click Add


## License and copyright

java-otp is published under the [MIT License](https://opensource.org/licenses/MIT).
