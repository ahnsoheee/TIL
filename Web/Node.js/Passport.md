## Passport

- Node.js Express의 인증 미들웨어
- 로그인을 쉽게 할 수 있도록 도와주는 역할
- naver, google, facebook 등 SNS를 통해 로그인할 수 있는 패키지가 있다.
- passport는 내부적으로 session을 사용하기 때문에, 미들웨어의 장착 순서(app.use)가 반드시 session 뒤에 존재해야 한다.

    ```jsx
    app.use(session({
      secret:"#JDKLF439jsdlfsjl",
      resave:false,
      saveUninitialized:true,
      store: sessionStore
    }))

    var passport = require('passport')
      , LocalStrategy = require('passport-local').Strategy;
    ```


### strategy
- 어떤 방식을 사용하는지 ex)  '/login'과 같은 경로
- 로그인이 성공했을 때와 실패했을 때의 redirection을 각각 지정할 수 있다.

    ```jsx
    app.post('/login', passport.authenticate('local', {
        successRedirect: '/',
        failureRedirect: '/login'
        failureFlash: true
        })
    );
    ```

- local
    - 아이디와 패스워드를 가지고 로그인하는 방식
    - local 외의 방식은 google, naver 등을 이용해 로그인하는 방식


### passport.serializeUser()

- 로그인이 성공했을 때 한 번 실행되는 메소드
- 식별자를 세션에 저장한다.
- req.session 객체에 어떤 데이터를 저장할지 선택한다.


### passport.deserializeUser()

- 페이지를 이동할 때마다(passport.session()이 실행될 때마다) 호출된다.
- 저장된 데이터를 조회할 때 사용한다.


### passport.use()
- 두번째 인자에서 실제 전략을 수행할 로직을 작성한다.
- 사용자 인증 로직 등


## 예시 코드
```js
router.use(session({
  secret: process.env.SECRET,
  resave: false,
  saveUninitialized: true,
  cookie: {
    secure: false
  }
}))

router.use(passport.initialize())
router.use(passport.session())


passport.serializeUser((id, done) => {
  done(null, id)
})

passport.deserializeUser((id, done) => {
  console.log('deserialized', id)
  User.findById.then(user => done(err, user))
})

passport.use(new LocalStrategy({
  usernameField: 'id',
  passwordField: 'pw',
  session: true
},
  function (id, pw, done) {
    return User.findUser(id, pw)
      .then(user => {
        if (user.length === 0) {
          return done(null, false, { message: 'Incorrect email or password' })
        }
        return done(null, user.id, { message: 'Logged In Successfully' })
      })
      .catch(err => done.log(err))
  }))

router.post('/login', passport.authenticate('local', {
  successRedirect: '/',
  failureRedirect: '/users/login',
  failureFlash: true
}))
```