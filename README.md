# 🎯 Flutter Layered Architecture Guide

| MIT                                                        | GPLv3                                                            | AGPL                                                        |
| ---------------------------------------------------------- | ---------------------------------------------------------------- | ----------------------------------------------------------- |
| ![MIT](https://img.shields.io/badge/License-MIT-green.svg) | ![GPL](https://img.shields.io/badge/License-GPL%20v3-yellow.svg) | ![AGPL](https://img.shields.io/badge/license-AGPL-blue.svg) |


A comprehensive guide to Flutter layered architecture, folder structures, and clean code patterns for scalable Flutter applications.

🎯 About This Guide
This repository is dedicated to Flutter layered architecture patterns, providing:

+ ✨ Clean Architecture: Proper separation of concerns in Flutter apps
+ 📁 Folder Structures: Scalable project organization patterns
+ 💻 Code Examples: Real Flutter implementations
+ 🌟 Best Practices: Proven patterns for Flutter development
+ 📦 Templates: Ready-to-use structures for new projects


## 📚 Table of Contents

+ 🎯 About This Guide
+ 🏗️ Architecture Overview
+ 📁 Folder Structures
+ 🔧 Layer Implementation
+ 📦 Dependencies Setup
+ 📄 License

## 🏗️ Architecture Overview

**Clean Architecture Layers**


```text
┌─────────────────┐
│   Presentation  │  ← UI, BLoC, Pages, Widgets
├─────────────────┤
│     Domain      │  ← Entities, UseCases, Repositories (Abstract)
├─────────────────┤
│      Data       │  ← Models, Repositories (Impl), DataSources
├─────────────────┤
│      Core       │  ← Utils, Constants, Error Handling
└─────────────────┘
```
### 📁 Folder Structures

**1. Feature-First Architecture**

```
lib/
├── main.dart
├── app/
│   ├── app.dart
│   ├── router/
│   │   ├── app_router.dart
│   │   ├── route_names.dart
│   │   └── route_config.dart
│   ├── theme/
│   │   ├── app_theme.dart
│   │   ├── app_colors.dart
│   │   ├── app_text_styles.dart
│   │   └── app_dimensions.dart
│   └── constants/
│       ├── app_constants.dart
│       ├── api_endpoints.dart
│       └── asset_paths.dart
├── core/
│   ├── error/
│   │   ├── exceptions.dart
│   │   ├── failures.dart
│   │   └── error_handler.dart
│   ├── network/
│   │   ├── network_info.dart
│   │   ├── dio_client.dart
│   │   ├── api_service.dart
│   │   └── interceptors/
│   │       ├── auth_interceptor.dart
│   │       └── logging_interceptor.dart
│   ├── storage/
│   │   ├── local_storage.dart
│   │   ├── shared_preferences_service.dart
│   │   ├── secure_storage_service.dart
│   │   └── hive_service.dart
│   ├── utils/
│   │   ├── extensions/
│   │   │   ├── context_extensions.dart
│   │   │   ├── string_extensions.dart
│   │   │   ├── date_extensions.dart
│   │   │   └── widget_extensions.dart
│   │   ├── helpers/
│   │   │   ├── validators.dart
│   │   │   ├── formatters.dart
│   │   │   ├── image_helper.dart
│   │   │   └── permission_helper.dart
│   │   ├── enums/
│   │   │   ├── status_enum.dart
│   │   │   └── user_role_enum.dart
│   │   └── logger/
│   │       └── app_logger.dart
│   └── widgets/
│       ├── buttons/
│       │   ├── custom_elevated_button.dart
│       │   ├── custom_text_button.dart
│       │   └── loading_button.dart
│       ├── inputs/
│       │   ├── custom_text_field.dart
│       │   ├── password_field.dart
│       │   └── search_field.dart
│       ├── dialogs/
│       │   ├── confirmation_dialog.dart
│       │   ├── loading_dialog.dart
│       │   └── error_dialog.dart
│       ├── cards/
│       │   ├── info_card.dart
│       │   └── custom_card.dart
│       └── misc/
│           ├── loading_widget.dart
│           ├── error_widget.dart
│           ├── empty_state_widget.dart
│           └── shimmer_widget.dart
├── features/
│   ├── authentication/
│   │   ├── data/
│   │   │   ├── datasources/
│   │   │   │   ├── auth_local_datasource.dart
│   │   │   │   └── auth_remote_datasource.dart
│   │   │   ├── models/
│   │   │   │   ├── user_model.dart
│   │   │   │   ├── login_request_model.dart
│   │   │   │   ├── login_response_model.dart
│   │   │   │   └── register_request_model.dart
│   │   │   └── repositories/
│   │   │       └── auth_repository_impl.dart
│   │   ├── domain/
│   │   │   ├── entities/
│   │   │   │   ├── user_entity.dart
│   │   │   │   └── auth_token_entity.dart
│   │   │   ├── repositories/
│   │   │   │   └── auth_repository.dart
│   │   │   └── usecases/
│   │   │       ├── login_usecase.dart
│   │   │       ├── register_usecase.dart
│   │   │       ├── logout_usecase.dart
│   │   │       ├── forgot_password_usecase.dart
│   │   │       └── get_current_user_usecase.dart
│   │   └── presentation/
│   │       ├── bloc/
│   │       │   ├── auth_bloc.dart
│   │       │   ├── auth_event.dart
│   │       │   ├── auth_state.dart
│   │       │   ├── login/
│   │       │   │   ├── login_bloc.dart
│   │       │   │   ├── login_event.dart
│   │       │   │   └── login_state.dart
│   │       │   └── register/
│   │       │       ├── register_bloc.dart
│   │       │       ├── register_event.dart
│   │       │       └── register_state.dart
│   │       ├── pages/
│   │       │   ├── login_page.dart
│   │       │   ├── register_page.dart
│   │       │   ├── forgot_password_page.dart
│   │       │   └── otp_verification_page.dart
│   │       └── widgets/
│   │           ├── login_form.dart
│   │           ├── register_form.dart
│   │           ├── auth_header.dart
│   │           ├── social_login_buttons.dart
│   │           └── password_strength_indicator.dart
│   ├── home/
│   │   ├── data/
│   │   │   ├── datasources/
│   │   │   │   ├── home_local_datasource.dart
│   │   │   │   └── home_remote_datasource.dart
│   │   │   ├── models/
│   │   │   │   ├── dashboard_model.dart
│   │   │   │   └── statistics_model.dart
│   │   │   └── repositories/
│   │   │       └── home_repository_impl.dart
│   │   ├── domain/
│   │   │   ├── entities/
│   │   │   │   ├── dashboard_entity.dart
│   │   │   │   └── statistics_entity.dart
│   │   │   ├── repositories/
│   │   │   │   └── home_repository.dart
│   │   │   └── usecases/
│   │   │       ├── get_dashboard_data_usecase.dart
│   │   │       └── get_statistics_usecase.dart
│   │   └── presentation/
│   │       ├── bloc/
│   │       │   ├── home_bloc.dart
│   │       │   ├── home_event.dart
│   │       │   └── home_state.dart
│   │       ├── pages/
│   │       │   └── home_page.dart
│   │       └── widgets/
│   │           ├── dashboard_card.dart
│   │           ├── statistics_widget.dart
│   │           └── quick_actions.dart
│   ├── profile/
│   │   ├── data/
│   │   ├── domain/
│   │   └── presentation/
│   └── products/
│       ├── data/
│       ├── domain/
│       └── presentation/
└── injection/
    ├── injection_container.dart
    └── injection_modules/
        ├── core_module.dart
        ├── network_module.dart
        └── feature_modules/
            ├── auth_module.dart
            ├── home_module.dart
            └── profile_module.dart
```

**2. Layer-First Architecture (Alternative)**

```
lib/
├── main.dart
├── app/
├── data/
│   ├── datasources/
│   │   ├── auth/
│   │   ├── home/
│   │   └── profile/
│   ├── models/
│   │   ├── auth/
│   │   ├── home/
│   │   └── profile/
│   └── repositories/
│       ├── auth_repository_impl.dart
│       ├── home_repository_impl.dart
│       └── profile_repository_impl.dart
├── domain/
│   ├── entities/
│   │   ├── user_entity.dart
│   │   ├── product_entity.dart
│   │   └── order_entity.dart
│   ├── repositories/
│   │   ├── auth_repository.dart
│   │   ├── home_repository.dart
│   │   └── profile_repository.dart
│   └── usecases/
│       ├── auth/
│       ├── home/
│       └── profile/
├── presentation/
│   ├── bloc/
│   │   ├── auth/
│   │   ├── home/
│   │   └── profile/
│   ├── pages/
│   │   ├── auth/
│   │   ├── home/
│   │   └── profile/
│   └── widgets/
│       ├── auth/
│       ├── home/
│       └── profile/
└── core/
```

**3. Modular Architecture (Large Apps)**

```
lib/
├── main.dart
├── app/
├── core/
├── shared/
│   ├── widgets/
│   ├── models/
│   ├── services/
│   └── utils/
└── modules/
    ├── auth/
    │   ├── auth_module.dart
    │   ├── data/
    │   ├── domain/
    │   ├── presentation/
    │   └── injection/
    ├── user/
    │   ├── user_module.dart
    │   ├── data/
    │   ├── domain/
    │   ├── presentation/
    │   └── injection/
    └── product/
        ├── product_module.dart
        ├── data/
        ├── domain/
        ├── presentation/
        └── injection/
```

**🔧 Layer Implementation**
## Data Layer Components

+ DataSource (Remote)

```
abstract class AuthRemoteDataSource {
  Future<LoginResponseModel> login(LoginRequestModel request);
  Future<UserModel> getCurrentUser();
  Future<void> logout();
}

class AuthRemoteDataSourceImpl implements AuthRemoteDataSource {
  final ApiService _apiService;
  
  AuthRemoteDataSourceImpl({required ApiService apiService})
      : _apiService = apiService;
  
  @override
  Future<LoginResponseModel> login(LoginRequestModel request) async {
    try {
      final response = await _apiService.post(
        ApiEndpoints.login,
        data: request.toJson(),
      );
      return LoginResponseModel.fromJson(response.data);
    } catch (e) {
      throw ServerException(message: e.toString());
    }
  }
}
```

+ DataSource (Local)

```
abstract class AuthLocalDataSource {
  Future<void> saveToken(String token);
  Future<String?> getToken();
  Future<void> saveUser(UserModel user);
  Future<UserModel?> getCachedUser();
  Future<void> clearAuthData();
}

class AuthLocalDataSourceImpl implements AuthLocalDataSource {
  final SharedPreferencesService _prefs;
  final SecureStorageService _secureStorage;
  
  AuthLocalDataSourceImpl({
    required SharedPreferencesService prefs,
    required SecureStorageService secureStorage,
  }) : _prefs = prefs, _secureStorage = secureStorage;
  
  @override
  Future<void> saveToken(String token) async {
    await _secureStorage.write(key: 'auth_token', value: token);
  }
  
  @override
  Future<String?> getToken() async {
    return await _secureStorage.read(key: 'auth_token');
  }
}
```

+ Model Classes

```
class UserModel extends UserEntity {
  const UserModel({
    required String id,
    required String name,
    required String email,
    String? avatar,
  }) : super(id: id, name: name, email: email, avatar: avatar);
  
  factory UserModel.fromJson(Map<String, dynamic> json) {
    return UserModel(
      id: json['id'] as String,
      name: json['name'] as String,
      email: json['email'] as String,
      avatar: json['avatar'] as String?,
    );
  }
  
  Map<String, dynamic> toJson() {
    return {
      'id': id,
      'name': name,
      'email': email,
      'avatar': avatar,
    };
  }
  
  UserModel copyWith({
    String? id,
    String? name,
    String? email,
    String? avatar,
  }) {
    return UserModel(
      id: id ?? this.id,
      name: name ?? this.name,
      email: email ?? this.email,
      avatar: avatar ?? this.avatar,
    );
  }
}
```
+ Repository Implementation

```
class AuthRepositoryImpl implements AuthRepository {
  final AuthRemoteDataSource _remoteDataSource;
  final AuthLocalDataSource _localDataSource;
  final NetworkInfo _networkInfo;
  
  AuthRepositoryImpl({
    required AuthRemoteDataSource remoteDataSource,
    required AuthLocalDataSource localDataSource,
    required NetworkInfo networkInfo,
  }) : _remoteDataSource = remoteDataSource,
       _localDataSource = localDataSource,
       _networkInfo = networkInfo;
  
  @override
  Future<Either<Failure, UserEntity>> login({
    required String email,
    required String password,
  }) async {
    if (!await _networkInfo.isConnected) {
      return Left(NetworkFailure(message: 'No internet connection'));
    }
    
    try {
      final request = LoginRequestModel(email: email, password: password);
      final response = await _remoteDataSource.login(request);
      
      await _localDataSource.saveToken(response.token);
      await _localDataSource.saveUser(response.user);
      
      return Right(response.user);
    } on ServerException catch (e) {
      return Left(ServerFailure(message: e.message));
    } catch (e) {
      return Left(UnknownFailure(message: e.toString()));
    }
  }
}
```

## Domain Layer Components

+ Entity class 

```
class UserEntity extends Equatable {
  final String id;
  final String name;
  final String email;
  final String? avatar;
  
  const UserEntity({
    required this.id,
    required this.name,
    required this.email,
    this.avatar,
  });
  
  @override
  List<Object?> get props => [id, name, email, avatar];
}
```

+ Repository Interface

```
abstract class AuthRepository {
  Future<Either<Failure, UserEntity>> login({
    required String email,
    required String password,
  });
  
  Future<Either<Failure, UserEntity>> register({
    required String name,
    required String email,
    required String password,
  });
  
  Future<Either<Failure, Unit>> logout();
  
  Future<Either<Failure, UserEntity>> getCurrentUser();
  
  Stream<AuthState> get authStateChanges;
}
```

+ UseCase Classes

```
class LoginUseCase implements UseCase<UserEntity, LoginParams> {
  final AuthRepository _repository;
  
  LoginUseCase({required AuthRepository repository})
      : _repository = repository;
  
  @override
  Future<Either<Failure, UserEntity>> call(LoginParams params) async {
    return await _repository.login(
      email: params.email,
      password: params.password,
    );
  }
}

class LoginParams extends Equatable {
  final String email;
  final String password;
  
  const LoginParams({
    required this.email,
    required this.password,
  });
  
  @override
  List<Object> get props => [email, password];
}
```

## Presentation Layer Components
+  BLoC Pattern

```
// Events
abstract class AuthEvent extends Equatable {
  @override
  List<Object> get props => [];
}

class LoginRequested extends AuthEvent {
  final String email;
  final String password;
  
  LoginRequested({required this.email, required this.password});
  
  @override
  List<Object> get props => [email, password];
}

class LogoutRequested extends AuthEvent {}

-------------------------------------------------------------------

// States
abstract class AuthState extends Equatable {
  @override
  List<Object?> get props => [];
}

class AuthInitial extends AuthState {}

class AuthLoading extends AuthState {}

class AuthAuthenticated extends AuthState {
  final UserEntity user;
  
  AuthAuthenticated({required this.user});
  
  @override
  List<Object> get props => [user];
}

class AuthUnauthenticated extends AuthState {}

class AuthError extends AuthState {
  final String message;
  
  AuthError({required this.message});
  
  @override
  List<Object> get props => [message];
}

-------------------------------------------------------------------


// BLoC
class AuthBloc extends Bloc<AuthEvent, AuthState> {
  final LoginUseCase _loginUseCase;
  final LogoutUseCase _logoutUseCase;
  final GetCurrentUserUseCase _getCurrentUserUseCase;
  
  AuthBloc({
    required LoginUseCase loginUseCase,
    required LogoutUseCase logoutUseCase,
    required GetCurrentUserUseCase getCurrentUserUseCase,
  }) : _loginUseCase = loginUseCase,
       _logoutUseCase = logoutUseCase,
       _getCurrentUserUseCase = getCurrentUserUseCase,
       super(AuthInitial()) {
    on<LoginRequested>(_onLoginRequested);
    on<LogoutRequested>(_onLogoutRequested);
  }
  
  Future<void> _onLoginRequested(
    LoginRequested event,
    Emitter<AuthState> emit,
  ) async {
    emit(AuthLoading());
    
    final result = await _loginUseCase(
      LoginParams(email: event.email, password: event.password),
    );
    
    result.fold(
      (failure) => emit(AuthError(message: failure.message)),
      (user) => emit(AuthAuthenticated(user: user)),
    );
  }
}
```
+ Page structure or Screen Overview

```
class LoginPage extends StatelessWidget {
  const LoginPage({Key? key}) : super(key: key);
  
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: BlocProvider(
        create: (context) => getIt<AuthBloc>(),
        child: const LoginView(),
      ),
    );
  }
}

class LoginView extends StatefulWidget {
  const LoginView({Key? key}) : super(key: key);
  
  @override
  State<LoginView> createState() => _LoginViewState();
}

class _LoginViewState extends State<LoginView> {
  final _formKey = GlobalKey<FormState>();
  final _emailController = TextEditingController();
  final _passwordController = TextEditingController();
  
  @override
  Widget build(BuildContext context) {
    return BlocConsumer<AuthBloc, AuthState>(
      listener: (context, state) {
        if (state is AuthError) {
          ScaffoldMessenger.of(context).showSnackBar(
            SnackBar(content: Text(state.message)),
          );
        } else if (state is AuthAuthenticated) {
          context.go('/home');
        }
      },
      builder: (context, state) {
        return Padding(
          padding: const EdgeInsets.all(16.0),
          child: Form(
            key: _formKey,
            child: Column(
              children: [
                const AuthHeader(),
                const SizedBox(height: 32),
                LoginForm(
                  emailController: _emailController,
                  passwordController: _passwordController,
                  onLogin: () => _onLogin(context),
                ),
                if (state is AuthLoading)
                  const CircularProgressIndicator(),
              ],
            ),
          ),
        );
      },
    );
  }
  
  void _onLogin(BuildContext context) {
    if (_formKey.currentState!.validate()) {
      context.read<AuthBloc>().add(
        LoginRequested(
          email: _emailController.text,
          password: _passwordController.text,
        ),
      );
    }
  }
}
```

+ 📦 Dependencies Setup
pubspec.yaml

```
dependencies:
  flutter:
    sdk: flutter
  
  # State Management
  flutter_bloc: ^8.1.3
  equatable: ^2.0.5
  
  # Dependency Injection
  get_it: ^7.6.4
  injectable: ^2.3.2
  
  # Network
  dio: ^5.3.2
  connectivity_plus: ^5.0.1
  
  # Local Storage
  shared_preferences: ^2.2.2
  flutter_secure_storage: ^9.0.0
  hive: ^2.2.3
  hive_flutter: ^1.1.0
  
  # Functional Programming
  dartz: ^0.10.1
  
  # Navigation
  go_router: ^12.1.3
  
  # Code Generation
  json_annotation: ^4.8.1
  freezed_annotation: ^2.4.1
  
  # UI
  cached_network_image: ^3.3.0
  shimmer: ^3.0.0

dev_dependencies:
  flutter_test:
    sdk: flutter
  
  # Code Generation
  build_runner: ^2.4.7
  json_serializable: ^6.7.1
  injectable_generator: ^2.4.1
  freezed: ^2.4.6
  
  # Testing
  mockito: ^5.4.2
  bloc_test: ^9.1.4
  
  # Linting
  flutter_lints: ^3.0.1
```

# refer this blog for detailed overview 

https://genai-blog.hashnode.dev/introduction-to-clean-architecture-for-flutter-beginners


## Authors

- [@vedantsagolale]((https://github.com/C12VS01vedant))

## License

[MIT](https://choosealicense.com/licenses/mit/)
