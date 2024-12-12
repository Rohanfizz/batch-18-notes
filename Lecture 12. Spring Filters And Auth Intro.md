What are spring filters?

Code example
```java
package com.example.filtertest;
  
import jakarta.servlet.Filter;
import jakarta.servlet.FilterChain;
import jakarta.servlet.FilterConfig;
import jakarta.servlet.ServletException;
import jakarta.servlet.ServletRequest;
import jakarta.servlet.ServletResponse;
import jakarta.servlet.http.HttpServletRequest;
import java.io.IOException;
import org.springframework.core.annotation.Order;
import org.springframework.stereotype.Component;
  
@Component
@Order(1)
public class AuthFilter implements Filter {
  
  @Override
  public void init(final FilterConfig filterConfig) throws ServletException {
    Filter.super.init(filterConfig);
  }
  
  @Override
  public void doFilter(
    ServletRequest request,
    ServletResponse response,
    FilterChain chain
  ) throws IOException, ServletException {
    HttpServletRequest httprequest = (HttpServletRequest) request;
    String usrName = httprequest.getHeader("userName");
    System.out.println("Successfully authenticated user  " + usrName);
    chain.doFilter(request, response);
  }
  
  @Override
  public void destroy() {
    Filter.super.destroy();
  }
}
```

OncePerRequestFilter
```java
package com.example.filtertest;
  
import java.io.IOException;
  
import org.springframework.stereotype.Component;
import org.springframework.web.filter.OncePerRequestFilter;
  
import jakarta.servlet.FilterChain;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
  
@Component
public class AuthFilter extends OncePerRequestFilter {
  
  @Override
  protected void doFilterInternal(
    HttpServletRequest request,
    HttpServletResponse response,
    FilterChain filterChain
  ) throws ServletException, IOException {
    final String userName = request.getHeader("userName");
    System.out.println(userName);
    response.addHeader("isAuthenticated", "true");
    filterChain.doFilter(request, response);
  }
}
```

- **Signup Flow**:
    - Client sends `username` and `password` to `/signup`.
    - User is saved, and a success message is returned.
- **Login Flow**:
    - Client sends `username` and `password` to `/login`.
    - Server validates credentials and returns `JWT_TOKEN`.
- **Access Protected Endpoint**:
    - Client sends a request to `/protected` with the token in the `Authorization` header.
    - Filter checks the token:
        - If valid: Proceed to the controller.
        - If invalid: Respond with `401 Unauthorized`.

![[Untitled Diagram.drawio.svg]]