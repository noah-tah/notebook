https://github.com/paralleldrive/cuid2

Secure, collision-resistant ids optimized for horizontal scaling and performance. Next generation UUIDs.

Need unique ids in your app? Forget UUIDs and GUIDs which often collide in large apps. Use Cuid2, instead.

**Cuid2 is:**

- **Secure:** It's not feasible to guess the next id, existing valid ids, or learn anything about the referenced data from the id. Cuid2 uses multiple, independent entropy sources and hashes them with a security-audited, NIST-standard cryptographically secure hashing algorithm (Sha3).
- **Collision resistant:** It's extremely unlikely to generate the same id twice (by default, you'd need to generate roughly 4,000,000,000,000,000,000 ids ([`sqrt(36^(24-1) * 26) = 4.0268498e+18`](https://en.wikipedia.org/wiki/Birthday_problem#Square_approximation)) to reach 50% chance of collision.)
- **Horizontally scalable:** Generate ids on multiple machines without coordination.
- **Offline-compatible:** Generate ids without a network connection.
- **URL and name-friendly:** No special characters.
- **Fast and convenient:** No async operations. Won't introduce user-noticeable delays. Less than 5k, gzipped.
- **But not _too fast_:** If you can hash too quickly you can launch parallel attacks to find duplicates or break entropy-hiding. For unique ids, the fastest runner loses the security race.


# Supported in Prisma
- When defining your database schema in `schema.prisma` you can use CUID2 by using:
```
id    String      @default(cuid(2))
```