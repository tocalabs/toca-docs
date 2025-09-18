# Security

The security page allows you to specify security options for users logging in to your Toca platform.
A strong password policy is crucial for protecting user accounts and the entire platform from unauthorized access.

## Password Rules
Password rules enforce specific criteria that users must meet when creating or changing their passwords. These rules help to make passwords harder for attackers to guess or crack. 

Some general guidelines for password rules follow:
- Minimum length: We recommend a minimum of 8 characters, shorter passwords are more susceptible to brute force attacks
- We recommend enforcing uppercase and lowercase characters, and setting numbers and symbols to at least 1.
- The password blacklist can be used to prevent users from using common easily guessed passwords or previously breached passwords, these will obviously depend on what settings you have set above as well as relevancy to your company (As an example, if your company name was Microsoft, you might want to blacklist 'Microsoft1' or 'Microsoft2025').

## Account Lockout
Account lockout is a security measure that temporarily disables an account after a certain number of failed login attempts. This prevents attackers from continuously trying to guess a user's password.

- Maximum Attempts: We recommend setting the maximum number of login attempts to between 3 and 5. This provides a balance between user convenience and security. More than 5 attempts could allow attackers to make progress with brute-force attacks, while fewer than 3 could lead to frequent lockouts for legitimate users who simply mistype their password.
- Lockout Time: The lockout duration should be long enough to deter automated brute-force attacks but short enough to not be overly burdensome for a user who is locked out. You should also factor in your password strength rules and maximum attempts before setting this - the more attempts the user has had, the higher you can likely set your lockout time.