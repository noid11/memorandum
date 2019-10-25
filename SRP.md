# SRP (Secure Remote Password) 学習メモ

<!-- TOC -->

- [SRP (Secure Remote Password) 学習メモ](#srp-secure-remote-password-学習メモ)
- [SRP: Industry-Standard Strong Password Security](#srp-industry-standard-strong-password-security)
- [SRP: What Is It?](#srp-what-is-it)
- [SRP: About the Project](#srp-about-the-project)
- [SRP: Competitive Analysis](#srp-competitive-analysis)
- [SRP: Design Specifications](#srp-design-specifications)
- [Links](#links)

<!-- /TOC -->

# SRP: Industry-Standard Strong Password Security  

http://srp.stanford.edu/

Secure Remote Password プロトコルは、人間が記憶できる短いパスワードの安全なリモート認証を実行し、受動的および能動的なネットワーク攻撃にレジストします。
SRP はパスワードセキュリティ、ユーザーの利便性、および制限付きライセンスの自由という独自の組み合わせを提供するため、このタイプの最も広く標準化されたプロトコルであり、その結果、大小さまざまな商用およびオープンソースの組織で使用されています。さまざまなコンピューティングプラットフォームで、ほぼすべての種類の human-authenticated ネットワークトラフィックを保護します。

<details>
<summary>原文</summary>

The Secure Remote Password protocol performs secure remote authentication of short human-memorizable passwords and resists both passive and active network attacks. 
Because SRP offers this unique combination of password security, user convenience, and freedom from restrictive licenses, it is the most widely standardized protocol of its type, and as a result is being used by organizations both large and small, commercial and open-source, to secure nearly every type of human-authenticated network traffic on a variety of computing platforms.
</details>

このサイトは、 SRP 認証を製品に簡単に統合できるソフトウェアやツールへのリンクなど、 SRP に関する情報の情報センターとして機能します。
このようなプロジェクトの数はここ数年で急速に増加しているため、このサイトは網羅的なリストを維持することはできませんが、代わりに代表的なカテゴリの重要かつクリティカルなプロジェクトに焦点を当てます。

<details>
<summary>原文</summary>

This site serves as a clearinghouse of information about SRP, including links to software and tools that make it easy to integrate SRP authentication into your products. 
Since the number of such projects has grown so rapidly in the last few years, this site cannot maintain an exhaustive list, but will instead focus on important and critical projects in representative categories.
</details>


SRP サイファースイートは、 SSL/TLS での安全な相互パスワード認証のソリューションとして確立され、ある方法で人間が記録したパスワードに基づいて安全な通信セションを確立するという一般的な問題を解決する、これは暗号学的に堅実で、氷刃化されており、互いにレビューし合い、複数の相互運用実装が存在します。
すべての暗号プリミティブと同様に、ゼロから始めるよりも、既存の十分にテストされたパッケージを再利用する方がほとんど常に優れています。

<details>
<summary>原文</summary>

The SRP ciphersuites have become established as the solution for secure mutual password authentication in SSL/TLS, solving the common problem of establishing a secure communications session based on a human-memorized password in a way that is crytographically sound, standardized, peer-reviewed, and has multiple interoperating implementations. 
As with any crypto primitive, it is almost always better to reuse an existing well-tested package than to start from scratch. 
</details>

# SRP: What Is It?

http://srp.stanford.edu/whatisit.html

SRP は、セキュアなパスワードベースの認証およびキー交換プロトコルです。
クライアントソフトウェアのユーザーが小さなシークレット（パスワードなど）を記憶する必要があり、他の秘密情報を持たない場合、およびサーバーが各ユーザーの検証を行う場合、サーバーに対してクライアントを安全に認証を行えます。
クライアントを認証しますが、セキュリティが侵害されても、攻撃者がクライアントになりすますことはできません。
さらに、 SRP は、成功した認証の副産物として暗号的に強力なシークレットを交換します。これにより、二者は安全に通信できます。

<details>
<summary>原文</summary>

SRP is a secure password-based authentication and key-exchange protocol. 
It solves the problem of authenticating clients to servers securely, in cases where the user of the client software must memorize a small secret (like a password) and carries no other secret information, and where the server carries a verifier for each user, which allows it to authenticate the client but which, if compromised, would not allow the attacker to impersonate the client. 
In addition, SRP exchanges a cryptographically-strong secret as a byproduct of successful authentication, which enables the two parties to communicate securely. 
</details>

多くのパスワード認証ソリューションは、この問題を解決すると主張しており、常に新しいものが提案されています。
暗号化されていない平文パスワードの送信を回避するプロトコルを考案することでセキュリティを主張できますが、次の場合に安全性を維持するプロトコルを考案することは困難です。

- 攻撃者はプロトコルの完全な知識を持っている
- 攻撃者は一般的に使用されるパスワードの大きな辞書にアクセスできる
- 攻撃者はクライアントとサーバー間のすべての通信を盗聴できる
- 攻撃者はクライアントとサーバー間で任意のメッセージを傍受、変更、および偽造できる
- 相互に信頼できるサードパーティは利用できない

<details>
<summary>原文</summary>

Many password authentication solutions claim to solve this exact problem, and new ones are constantly being proposed. Although one can claim security by devising a protocol that avoids sending the plaintext password unencrypted, it is much more difficult to devise a protocol that remains secure when:

- Attackers have complete knowledge of the protocol.
- Attackers have access to a large dictionary of commonly used passwords.
- Attackers can eavesdrop on all communications between client and server.
- Attackers can intercept, modify, and forge arbitrary messages between client and server.
- A mutually trusted third party is not available. 
</details>

SRP の背後にあるアイデアは 1996 年後半に USENET で最初に登場し、その後の議論は 1997 年にこれらのセキュリティプロパティに対処するための洗練された提案につながりました。
暗号化関連のニュースグループとメーリングリストで議論と改良を繰り返した後、 1998 年に公開された SRP-3 として知られる、現在も使用されているプロトコルの1つが開発されました。
このテクノロジーは、SRP-6 に進化しました。 SRP-6 は、 SRP-3 のセキュリティを維持しますが、既存のシステムへの組み込みをより柔軟かつ容易にする改良点を備えています。
[実際のプロトコル設計の技術的な詳細](http://srp.stanford.edu/design.html "SRP Protocol Design")は、このサイトから入手できます。

<details>
<summary>原文</summary>

The idea behind SRP first appeared on USENET in late 1996, and subsequent discussion led to refined proposals in 1997 to address these security properties. 
This lead to the development of one of the variants of the protocol still in use today, known as SRP-3, which was published in 1998 after several rounds of discussion and refinement on cryptography-related newsgroups and mailing lists, and has withstood considerable public analysis and scrutiny since then. 
The technology evolved into a newer variant known as SRP-6, which maintains the security of SRP-3 but has refinements that make it more flexible and easier to incorporate into existing systems. 
Technical details of the actual protocol design are available from this site. 
</details>

SRP は、[ロイヤリティフリーライセンス](http://srp.stanford.edu/license.txt "Licensing")の下で、商用および非商用ユーザーが利用できます。
インターネットは、SRP の初期の開発において重要な役割を果たしました。インターネットなしでは、 SRP は最初に提案および改良されてから得られた分析とフィードバックを受け取れなかったでしょう。
したがって、インターネット全体がこの努力の成果から利益を得ることができるのは適切です。
SRP は、この分野の既存特許を回避するように設計されているため、誰もがさまざまな用途に使用できる強力で邪魔にならないパスワード認証技術にアクセスできます。

<details>
<summary>原文</summary>

SRP is available to commercial and non-commercial users under a royalty-free license. 
The Internet played a significant role in SRP's early development; without it, SRP would not have received anywhere near the amount of analysis and feedback that it has gotten since it was first proposed and refined. 
It is thus fitting that the Internet at large can benefit from the fruits of this endeavor.
Since SRP is specifically designed to work around existing patents in the area, it gives everybody access to strong, unencumbered password authentication technology that can be put to a wide variety of uses. 
</details>

SRP ディストリビューションは、オープンソースに優しいライセンス条件で利用できます（ net.savvy リーダーの場合、「BSDスタイル」ライセンスです）。 
[SRP プロジェクトの詳細](http://srp.stanford.edu/project.html "The SRP Project")については、このサイトで入手できます。また、 SRP サポートを組み込んだ Telnet および FTP のバージョンを含む[リファレンス実装](http://srp.stanford.edu/download.html "SRP Open-Source Software")もダウンロードできます。
[リンクページ](http://srp.stanford.edu/references.html#links "Password Authentication References")には、 SRP を使用する商用および非商用の幅広いプロジェクトと製品へのポインタ、および強力なパスワード認証をカバーする関連作業と論文があります。

<details>
<summary>原文</summary>

The SRP distribution is available under Open Source-friendly licensing terms (for the net.savvy reader, it's a "BSD-style" license). More information about the SRP project is available at this site, and a reference implementation, which includes versions of Telnet and FTP that incorporate SRP support, can be downloaded as well. 
The links page has pointers to a wide range of projects and products, both commercial and non-commercial, that use SRP, as well as related work and papers that cover strong password authentication. 
</details>

# SRP: About the Project

http://srp.stanford.edu/project.html

SRP プロジェクトは、 1997 年にスタンフォード大学で Java ベースの Webtop プロジェクトの認証システムとして開始されました。
それ以来、世界中の開発者がプロジェクトに貢献し、本格的なインターネット全体のオープンソースプロジェクトに進化しました。
さらに SRP は、安全な無料のパスワード認証ソリューションとして、世界中の大学、企業、および組織の商用、非商用、およびスタンドアロン構成で展開されています。

<details>
<summary>原文</summary>

The SRP Project was started in 1997 at Stanford University as an authentication system for a Java-based webtop project. Since then, it has evolved into a full-fledged Internet-wide Open Source project, with developers from around the world contributing to the Project. 
In addition, SRP has been deployed as a secure, free password authentication solution in commercial, non-commercial, and standalone configurations in universities, companies, and organizations worldwide.
</details>

SRP プロジェクトの主な目標は、既存のプロトコルとアプリケーションのパスワードセキュリティを向上させると同時に、パスワードに関連する使いやすさを維持し、これらのシステムと完全に統合する標準、技術、実装を提供することです。
SRP は多くの考慮事項を念頭に置いて設計されているため、これらの目的を達成します。

<details>
<summary>原文</summary>

The primary goal of the SRP Project is to provide standards, technologies, and implementations that improve password security of existing protocols and applications while preserving the ease-of-use associated with passwords and integrating cleanly with these systems. 
SRP accomplishes these objectives because it was designed with a number of considerations in mind. 
</details>

**セキュリティ** - SRP は、パッシブネットワーク攻撃とアクティブネットワーク攻撃の両方からパスワードを保護するように設計されました。 
このプロジェクトでは、オープンリサーチと発表は、独自のクローズドソース開発よりも真に安全な暗号システムを生み出す可能性が高いと考えています。
1997 年に導入され、1998 年に公開されて以来、 SRP は広く分析および研究されており、これまでのすべての分析によりセキュリティが裏付けられています。
パスワードセキュリティは活発な研究分野であり、 SRP はその基礎となる数学的基盤（離散対数）に対する暗号解析の進歩の影響を受けることを認識しています。

<details>
<summary>原文</summary>

**Security** - SRP was designed to protect passwords against both passive and active network attacks. 
The Project believes that open research and publication is more likely to produce a truly secure cryptosystem than proprietary, closed-source development. 
Since its introduction in 1997 and publication in 1998, SRP has been extensively analyzed and studied in the open, and all analysis to date has confirmed its security. 
We realize that password security is an active field of research and that SRP is subject to cryptanalytic advances against its underlying mathematical foundations (discrete logarithms). 
</details>

**利便性** - 一部のユーザーの観点から見ると、SRP がパスワードインターフェイスをまったく同じに保ちながら安全な認証を提供しているという事実は、おそらくその技術的進歩の中で最大のものです。
これまで、ユーザーは妥協する必要がありました - 追加の不便さを我慢するか、不完全なセキュリティモデルを受け入れる等。
SRP は両方向で現状を前進させ、1つのパッケージで両方の長所を実現します。

<details>
<summary>原文</summary>

**Convenience** - From the perspective of some users, the fact that SRP keeps password interfaces exactly the same while delivering secure authentication is perhaps the greatest of its technical advances. 
Until now, users have had to compromise - either put up with some added inconvenience or accept an imperfect security model. 
SRP advances the status quo in both directions, achieving the best of both worlds in one package. 
</details>

**オープン性** - オープンソースソフトウェアの重要性が増すにつれて、フリーウェアコミュニティが暗号技術を利用できるようにすることが重要です。
SRP はオープンソースフレンドリーな条件で配布されるため、このようなプロジェクトはこの技術を活用できます。

<details>
<summary>原文</summary>

**Openness** - With the increasing importance of Open Source software, it is important that cryptographic technology remain available to the freeware community. 
SRP is distributed on Open Source-friendly terms so that such projects can take advantage of the technology. 
</details>

**シンプルさ** - SRP は、弱いパスワード認証の代替品です。
サードパーティ、キーサーバー、または PKI を使用する代わりに、 SRP はユーザーからパスワードを受け取り、その結果として安全な認証とキー交換を生成する単なるブラックボックスです。
主要なインターフェースの変更を必要としない「より良いマウストラップ」であるため、様々なプロダクトは SRP を単一の独自のモノリシックエンティティとして残す代わりに、 SRP を組み込むことができます。

<details>
<summary>原文</summary>

**Simplicity** - SRP is a drop-in replacement for weak password authentication. 
Instead of involving third parties, key servers, or a PKI, SRP is just a black box that accepts a password from the user and produces secure authentication and key-exchange as its result. 
Since it is a "better mousetrap" that doesn't require major interface changes, a wide range of products have been able to incorporate SRP instead of having it remain as a single, proprietary, monolithic entity. 
</details>

オープンソースの動きは、この目的の重要な部分です。なぜなら、オープンソース OS が自由に利用可能な新しいテクノロジーを統合する能力は、最大の強みの1つだからです。
SRP は、輸出規制を受けることなく米国ベースのソフトウェアに組み込むことができるため、これにより、すべてのユーザーに利益をもたらす可能性のあるレベルのユニバーサルパスワードセキュリティが可能になります。
実際、これらの OS（Linux や OpenBSD など）のユーザーは、まさにこのタイプの統合に大きな関心を示しています。

<details>
<summary>原文</summary>

The Open Source movement is an important part of this objective, because the ability of Open Source OSes to integrate new, freely-available technology is one of its greatest strengths. 
Because SRP can be incorporated into US-based software without being subject to export restrictions, this enables the level of universal password security that has the potential to benefit all users. 
Indeed, users of these OSes (e.g. Linux and OpenBSD) have expressed a great deal of interest in exactly this type of integration. 
</details>


# SRP: Competitive Analysis
http://srp.stanford.edu/analysis.html


# SRP: Design Specifications

http://srp.stanford.edu/design.html

SRP は、強力な認証プロトコルの新しいクラスに新しく追加されたもので、ネットワークを介したすべての有名な受動的および能動的な攻撃にレジストします。
SRP は他のキー交換および識別プロトコルからいくつかの要素を借用し、いくつかの微妙な修正と改良を追加します。
その結果、 EKE ファミリーのプロトコルの強度と効率を維持しながら、それらの欠点のいくつかを修正するプロトコルができました。

<details>
<summary>原文</summary>

SRP is the newest addition to a new class of strong authentication protocols that resist all the well-known passive and active attacks over the network. 
SRP borrows some elements from other key-exchange and identification protcols and adds some subtle modifications and refinements. 
The result is a protocol that preserves the strength and efficiency of the EKE family protocols while fixing some of their shortcomings. 
</details>


# Links 

SRP: Industry-Standard Strong Password Security  
http://srp.stanford.edu/

Secure Remote Password protocol - Wikipedia  
https://en.wikipedia.org/wiki/Secure_Remote_Password_protocol

Secure Remote Password (SRP) Protocol  
https://sehermitage.web.fc2.com/crypto/SRP.html