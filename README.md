// admin.routes.js

const auditMiddleware =
  require(
    "../middleware/audit.middleware"
  );

router.put(
  "/change-role/:id",

  authMiddleware,

  permissionMiddleware(
    "EDIT_ADMIN"
  ),

  auditMiddleware(
    "ADMIN_MANAGEMENT",
    "CHANGE_ROLE",
    "role",

    async () => "USER",

    async (req) =>
      req.body.role
  ),

  controller.changeRole
);