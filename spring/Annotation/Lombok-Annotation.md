Lombok Annotation
==========

> @NoArgsConstructor
```text
- 기본생성자를 생성
```

> @AllArgsConstructor
```text
- 클래스에 존재하는 모든 field에 대한 생성자를 생성
```

> @RequiredArgsConstructor
```text
- final이나 @NonNull인 필드 값만 파라미터로 받는 생성자를 생성
```

> @Getter
```text
- 클래스 내 모든 필드의 Getter 메서드 생성
```

> @Setter
```text
- 클래스 내 모든 필드의 Setter 메서드 생성한다.
```

> @ToString
```text
- 클래스 내 모든 필드의 toString 메서드 생성
```

> @EqualsAndHashCode
```text
- equals와 hashCode 메서드 생성
```

> @Data
```text
- @Getter @Setter @EqualsAndHashCode @AllArgsConstructor을 포함한 Lombok에서 제공하는 필드와 관련된 모든 코드를 생성
```