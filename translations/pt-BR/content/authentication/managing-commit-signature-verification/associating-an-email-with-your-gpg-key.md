---
title: Associar um e-mail à chave GPG
intro: 'Sua chave GPG deve ser associada a um e-mail verificado do {% data variables.product.product_name %} que corresponda à identidade do committer.'
redirect_from:
  - /articles/associating-an-email-with-your-gpg-key
  - /github/authenticating-to-github/associating-an-email-with-your-gpg-key
  - /github/authenticating-to-github/managing-commit-signature-verification/associating-an-email-with-your-gpg-key
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Identity
  - Access management
shortTitle: Associar e-mail com a chave GPG
---

{% note %}

Se você estiver usando uma chave GPG que corresponde à sua identidade do autor do submissão e ao endereço de e-mail verificado associado à sua conta em {% ifversion ghae %}{% data variables.product.product_name %}{% else %}{% data variables.product.product_location %}{% endif %}, você poderá começar a assinar commits e tags.

{% endnote %}

{% data reusables.command_line.open_the_multi_os_terminal %}
{% data reusables.gpg.list-keys-with-note %}
{% data reusables.gpg.copy-gpg-key-id %}
4. Insira `gpg --edit-key GPG key ID`, substituindo a ID da chave GPG que deseja usar. No seguinte exemplo, a ID da chave GPG é `3AA5C34371567BD2`:
  ```shell
  $ gpg --edit-key <em>3AA5C34371567BD2</em>
  ```
5. Digite `gpg> adduid` para adicionar os detalhes da ID do usuário.
  ```shell
  $ gpg> adduid
  ```
6. Siga as solicitações para fornecer seu nome verdadeiro, endereço de e-mail e quaisquer comentários. Você pode modificar as entradas escolhendo `N`, `C` ou `E`. {% data reusables.gpg.private-email %} {% ifversion fpt or ghec %} Para obter mais informações, consulte "[Configurar o endereço de e-mail do commit](/articles/setting-your-commit-email-address)."{% endif %}
  ```shell
  Real Name: <em>Octocat</em>
  Email address: <em>octocat@github.com</em>
  Comment: <em>GitHub key</em>
  Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?
  ```
7. Insira `O` para confirmar suas seleções.
8. Insira a frase secreta da sua chave.
9. Insira `gpg> salvar` para salvar as alterações
  ```shell
  $ gpg> save
  ```
10. Digite `gpg --armor --export GPG key ID`, substituindo a ID da chave GPG que deseja usar. No seguinte exemplo, a ID da chave GPG é `3AA5C34371567BD2`:
  ```shell
  $ gpg --armor --export <em>3AA5C34371567BD2</em>
  # Prints the GPG key, in ASCII armor format
  ```
11. Faça upload da chave GPG [adicionando-a à sua conta do GitHub](/articles/adding-a-gpg-key-to-your-github-account).

## Leia mais

- "[Verificar se há chaves GPG existentes](/articles/checking-for-existing-gpg-keys)"
- "[Gerar uma nova chave GPG](/articles/generating-a-new-gpg-key)"
- "[Usar um endereço de e-mail verificado na chave GPG](/articles/using-a-verified-email-address-in-your-gpg-key)"
- "[Adding a GPG key to your GitHub account](/articles/adding-a-gpg-key-to-your-github-account)"
- "[Assinar commits](/articles/signing-commits)"
- "[Assinar tags](/articles/signing-tags)"
